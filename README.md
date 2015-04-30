# Hazza
Hazza
pod "VK-ios-sdk" 
-(BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation 
{ 
    [VKSdk processOpenURL:url fromApplication:sourceApplication]; 
    return YES; 
} 
[VKSdk initializeWithDelegate:delegate andAppId:YOUR_APP_ID]; 
    if ([VKSdk wakeUpSession]) 
    { 
        //Start working 
    }
[VKSdk authorize:scope]; 
[VKSdk authorize:scope revokeAccess:YES]; 
[VKSdk authorize:scope revokeAccess:YES forceOAuth:YES]; 
-(void) vkSdkReceivedNewToken:(VKAccessToken*) newToken; 
-(void) vkSdkUserDeniedAccess:(VKError*) authorizationError; 
VKRequest * audioReq = [[VKApi users] get]; 
VKRequest * audioReq = [[VKApi audio] get:@{VK_API_OWNER_ID : @"896232"}]; 
VKRequest * audioReq = [[VKApi audio] get:@{VK_API_OWNER_ID : @"896232"}]; 
audioReq.secure = NO; 
VKRequest * postReq = [[VKApi wall] post:@{VK_API_MESSAGE : @"Test"}]; 
postReq.attempts = 10; 
//or infinite 
//postReq.attempts = 0; 
VKRequest * getWall = [VKRequest requestWithMethod:@"wall.get" andParameters:@{VK_API_OWNER_ID : @"-1"} andHttpMethod:@"GET"]; 
VKRequest * request = [VKApi uploadWallPhotoRequest:[UIImage imageNamed:@"my_photo"] parameters:[VKImageParameters pngImage] userId:0 groupId:0 ]; 

[audioReq executeWithResultBlock:^(VKResponse * response) { 
       NSLog(@"Json result: %@", response.json); 
} errorBlock:^(NSError * error) { 
       if (error.code != VK_API_ERROR) { 
             [error.vkError.request repeat]; 
       } 
      else { 
             NSLog(@"VK error: %@", error); 
       } 
}]; 
-(void) vkSdkNeedCaptchaEnter:(VKError*) captchaError 
{ 
    VKCaptchaViewController * vc = [VKCaptchaViewController captchaControllerWithError:captchaError]; 
    [vc presentIn:self]; 
} 
VKRequest * request1 = [[VKApi audio] get]; 
 request1.completeBlock = ^(VKResponse*) { ... }; 

VKRequest * request2 = [[VKApi users] get:@{VK_USER_IDS : @[@(1), @(6492), @(1708231)]}]; 
request2.completeBlock = ^(VKResponse*) { ... }; 
VKBatchRequest * batch = [[VKBatchRequest alloc] initWithRequests:request1, request2, nil]; 
[batch executeWithResultBlock:^(NSArray *responses) { 
        NSLog(@"Responses: %@", responses); 
 } errorBlock:^(NSError *error) { 
        NSLog(@"Error: %@", error); 
 }]; 
 VKShareDialogController * shareDialog = [VKShareDialogController new]; //1 
shareDialog.text = @"This post created using #vksdk #ios"; //2 
shareDialog.vkImages = @[@"-10889156_348122347",@"7840938_319411365",@"-60479154_333497085"]; //3 
shareDialog.shareLink = [[VKShareLink alloc] initWithTitle:@"Super puper link, but nobody knows" link:[NSURL URLWithString:@"https://vk.com/dev/ios_sdk"]]; //4 
[shareDialog setCompletionHandler:^(VKShareDialogControllerResult result) { 
    [self dismissViewControllerAnimated:YES completion:nil]; 
}]; //5 
[self presentViewController:shareDialog animated:YES completion:nil]; //6
NSArray *items = @[[UIImage imageNamed:@"apple"], @"Check out information about VK SDK" , [NSURL URLWithString:@"https://vk.com/dev/ios_sdk"]]; //1 
UIActivityViewController *activityViewController = [[UIActivityViewController alloc] 
                                                    initWithActivityItems:items 
                                                    applicationActivities:@[ [VKActivity new] ] ]; //2 
[activityViewController setValue:@"VK SDK" forKey:@"subject"]; //3 
[activityViewController setCompletionHandler:nil]; //4 
if (VK_SYSTEM_VERSION_GREATER_THAN_OR_EQUAL_TO(@"8.0") && UIUserInterfaceIdiomPad == [[UIDevice currentDevice] userInterfaceIdiom]) { 
    UIPopoverPresentationController *popover = activityViewController.popoverPresentationController; 
    popover.sourceView = self.view; 
    popover.sourceRect = [tableView rectForRowAtIndexPath:indexPath]; 
} //5 
[self presentViewController:activityViewController animated:YES completion:nil]; //6
