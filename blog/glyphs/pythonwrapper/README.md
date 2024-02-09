# Backwards Compatibility

Today I worked on ensuring my Glyphs plugin works with older versions of Glyphs 3.

When I found something that broke on an earlier version I at first thought I'd have to go through the process of finding out which version it breaks on and then run different code based on which version of Glyphs the user is running.

As usual, the solution becomes a lot easier if you reframe your assumptions.

Since the error message complained about 'x' function missing from this class, I could probably just go and check if said class had said function.

This is where the Python "hasattr" and "callable"-methods come in handy.

For example, to intersect two shapes in Glyphs, there's a method called in the GSPathOperator called 'intersectPaths_with_error_', but previously it was called 'intersectPaths_from_error_'. This is what's called a breaking change.
To fix this, I can add some control flow statements to run the method based on whether or not the newer method is available.

´´´
    @objc.python_method
    def intersect(self, shapeTwo, shapeOne):
        GSPathOperator = NSClassFromString("GSPathOperator")
        if hasattr(GSPathOperator, 'intersectPaths_with_error_') and callable(
                GSPathOperator.intersectPaths_with_error_):
            GSPathOperator.intersectPaths_with_error_(shapeTwo, shapeOne, None)
        else:
            GSPathOperator.intersectPaths_from_error_(shapeTwo, shapeOne, None)
        return shapeOne
´´´

Switching between the older and newer version of Glyphs 3 I found at least three places where the Glyphs API changed.

In the absence of updated docs (which is normally the case in any project due to the infeasibility of perfectly updated docs), I find reflection and reverse engineering techniques to be a lifesaver.
