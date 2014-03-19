# KWTransition

Experimental Implementations of UIViewControllerAnimatedTransitioning.

## Requirements

- Objective-C ARC
- iOS 7 or above

## Installation
### Cocoapods

    pod 'KWTransition'

###Manual

You can manually install this library by copying the `KWTransition.h` and `KWTransition.m` into your project.

## Usage

1. Import the header.

        #import <KWTransition.h>

2. Implement delegate transitioning delegate on the initial view controller (the one doing the presenting).

        <UIViewControllerTransitioningDelegate>

3. Implement a transition manager property on the initial view controller.

        @property (nonatomic, strong) KWTransition *transition;

    Be sure to initialise the manager somewhere.
        
        _transition = [KWTransition manager];

4. Set the controller to use custom presentations

        [self setModalPresentationStyle: UIModalPresentationCustom];

5. Implement the transitioning delegate


        #pragma mark - UIVieControllerTransitioningDelegate
        - (id <UIViewControllerAnimatedTransitioning>)animationControllerForPresentedController:(UIViewController *)presented
								                                           presentingController:(UIViewController *)presenting
                                                                               sourceController:(UIViewController *)source {
	        self.transition.action = KWTransitionStepPresent;
	        return self.transition;
        }
        -(id<UIViewControllerAnimatedTransitioning>)animationControllerForDismissedController:(UIViewController *)dismissed {
	        self.transition.action = KWTransitionStepDismiss;
	        return self.transition;
        }

6. Select your animation and present!

        self.transition.style = KWTransitionStyleFadeBackOver;
	    KWModalViewController *VC = [[KWModalViewController alloc] init];
	    VC.transitioningDelegate = self;
	    [self presentViewController:VC animated:YES completion:nil];

## License

The MIT License (MIT)

Copyright (c) 2014 Kurt Wagner

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.


