# OCBorghettiView

![](http://f.cl.ly/items/2l3X2W1k1j2O3W213T1T/OCBorghettiView.png)

## Introduction

OCBorghettiView is an easy to use accordion view component for iOS. It was named after [Renato Borghetti](http://youtu.be/xfsaGLesNHE?t=24s), a Brazilian folk musician and composer who works on the traditional style from his home state of Rio Grande do Sul. Borghetti's main instrument is the diatonic button accordion (known as *gaita* in Brazilian Portuguese).

## Under the Hood

* Reusable by design
* Built for iPhone and iPad
* Uses ARC (Automatic Reference Counting)
* Supports device rotation
* Supports customization
* Supports UIViews as sections (UITableViews, UIWebView, MKMapView, etc...)

## How to install it?

[CocoaPods](http://cocoapods.org) is the easiest way to install OCBorghettiView. Run ```pod search OCBorghettiView``` to search for the latest version.

Then, copy and past the ```pod``` line to your ```Podfile```. Your podfile shall look like this:

```
platform :ios, '6.0'
pod 'OCBorghettiView', '~> 0.0.1'
```

Finally, install it running ```pod install```.

## How to contribute?

1. Fork and clone this project.
2. Make your changes (and add/modify specs for your changes)
3. Make sure all the specs are OK
4. Push to your fork and do a Pull Request.

## Interface

### OCBorghettiView Class

```objective-c
@interface OCBorghettiView : UIView

- (void)addSectionWithTitle:(NSString *)sectionTitle
                    andView:(id)sectionView;

@property (nonatomic, assign) NSInteger accordionSectionHeight;
@property (nonatomic, strong) UIColor *accordionSectionColor;
@property (nonatomic, strong) UIFont *accordionSectionFont;
@property (nonatomic, strong) UIColor *accordionSectionBorderColor;
@property (nonatomic, assign) id <OCBorghettiViewDelegate> delegate;

@end
```
    
### OCBorghettiViewDelegate Protocol

```objective-c
@protocol OCBorghettiViewDelegate <NSObject>

@optional

- (void)accordion:(OCBorghettiView *)accordion
 didSelectSection:(UIView *)view
        withTitle:(NSString *)title;

@end
```

# How to use it

```objective-c
- (void)viewDidLoad
{
    [super viewDidLoad];
    
	// Initialization
    OCBorghettiView *accordion = [[OCBorghettiView alloc] initWithFrame:frame];
	
	// Settings and colors
    accordion.accordionSectionHeight = 40;
    accordion.accordionSectionFont = [UIFont fontWithName:@"Avenir" size:16];
	accordion.accordionSectionBorderColor = [UIColor darkGrayColor];
	accordion.accordionSectionColor = [UIColor grayColor];
    
    [self.view addSubview:accordion];

    // Section One
    UIView *sectionOne = [[UIView alloc] init];
    [sectionOne setBackgroundColor:[UIColor redColor]];
    [accordion addSectionWithTitle:@"Section One"
                           andView:sectionOne];

    // Section Two
    UIView *sectionTwo = [[UIView alloc] init];
    [sectionTwo setBackgroundColor:[UIColor greenColor]];
    [accordion addSectionWithTitle:@"Section Two"
                           andView:sectionTwo];

    // Section Three
    UIView *sectionThree = [[UIView alloc] init];
    [sectionThree setBackgroundColor:[UIColor yellowColor]];
    [accordion addSectionWithTitle:@"Section Three"
                           andView:sectionThree];
}
```

## License

Copyright (c) 2012 Otavio Cordeiro. All rights reserved.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.