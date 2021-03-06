MTStringAttributes
==================

An easier way to create an attributes dictionary for NSAttributedString


## Installation

In your Podfile, add this line:

    pod "MTStringAttributes"

pod? => https://github.com/CocoaPods/CocoaPods/


## Example Usage

    #include <MTStringAttributes.h>

Create an attributes object

    MTStringAttributes *attributes = [[MTStringAttributes alloc] init];

Set some basic properties

    attributes.font             = nil;
    attributes.textColor        = [UIColor redColor];
    attributes.backgroundColor  = [UIColor blackColor];
    attributes.strikethrough    = YES;
    attributes.underline        = YES;

Some more advanced stuff

    attributes.ligatures        = YES;
    attributes.kern             = @(1);
    attributes.outlineColor     = [UIColor blueColor];
    attributes.outlineWidth     = @(2);

I might break out the properties for paragraph style later, but for now, provide an object

    NSParagraphStyle *ps        = [[NSParagraphStyle alloc] init]
    ps.alignment                = NSTextAlignmentLeft;
    attributes.paragraphStyle   = ps;

Shadow

    attributes.shadowBlurRadius = @(1.4);
    attributes.shadowColor      = [UIColor grayColor];
    attributes.shadowOffsetX    = @(0.2);
    attributes.shadowOffsetY    = @(0.3);

Finally

    NSAttributedString *str     = [[NSAttributedString alloc] initWithString:@"The attributed string!" attributes:[attributes dictionary]];


## Parser


Relying on [Slash](https://github.com/chrisdevereux/Slash), MTStringParser allows you to add styles to
tags and then generate attributed strings from markup of those tags.

```
#include <MTStringParser.h>

[[MTStringParser sharedParser] addStyleWithTagName:@"red" font:[UIFont systemFontOfSize:12] color:[UIColor redColor]];
NSAttributedString *string = [[MTStringParser sharedParser] attributedStringFromMarkup:@"This is a <red>red section</red>"];
```

## Contributing

Please update and run the tests before submitting a pull request. Thanks.

## Author

[Adam Kirk](https://github.com/atomkirk) ([@atomkirk](https://twitter.com/atomkirk))
