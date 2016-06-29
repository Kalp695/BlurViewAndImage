# BlurViewAndImage


  
  if (!UIAccessibilityIsReduceTransparencyEnabled()) {
        self.view.backgroundColor = [UIColor clearColor];
        
        UIBlurEffect *blurEffect = [UIBlurEffect effectWithStyle:UIBlurEffectStyleDark];
        UIVisualEffectView *blurEffectView = [[UIVisualEffectView alloc] initWithEffect:blurEffect];
        blurEffectView.frame = self.view.bounds;
        blurEffectView.autoresizingMask = UIViewAutoresizingFlexibleWidth | UIViewAutoresizingFlexibleHeight;
        
        [self.view addSubview:blurEffectView];
    }
    else {
        self.view.backgroundColor = [UIColor redColor];
    }
    
   
    UIImage *originalImage = [UIImage imageNamed:@"color"];
    CIImage *imageToBlur = [CIImage imageWithCGImage:originalImage.CGImage];
    
    CIFilter *gaussianBlurFilter = [CIFilter filterWithName: @"CIGaussianBlur"];
    [gaussianBlurFilter setValue:imageToBlur forKey: @"inputImage"];
    [gaussianBlurFilter setValue:[NSNumber numberWithFloat: 10] forKey: @"inputRadius"]; //change number to increase/decrease blur
    
    CIImage *resultImage = [gaussianBlurFilter valueForKey: @"outputImage"];
    
    
    
    UIImage *blurredImage = [[UIImage alloc] initWithCIImage:resultImage];
    
    UIImageView *blurredImageView = [[UIImageView alloc] initWithImage:blurredImage];
    
    [self.view addSubview:blurredImageView];
    
    }
