# MTTouchAndFaceID
- Now a days most of application require authentication in mobile domain for device owners to verify their identity by TouchID or FaceID. 
- And user also want to secure their data from anonymous user. 
- Apple introduced biometric authentication fingerprint scanner technology in iPhone 5s to allow users to unlock their devices and after that apple introduced iPhone X and iOS 11 biometric authentication using facial recognition.
- The TouchID/FaceID is on a new framework Local Authentication , It’s necessary to say that this framework which provides facilities for requesting authentication from users with specified securities policies.
- Local Authentication framework provide custom made view for users can enter credentials using TouchID or FaceID.
- So we create very simple file for authentication of your application and it is very easy to use just follow below steps.

## Requirements
- Swift 3.0+
- iOS 8.0+
- Xcode 8+

## Touch ID Screenshot

![alt text](https://github.com/manekdilip/MTTouchAndFaceID/blob/master/iPhone-TouchId.gif)
![alt text](https://github.com/manekdilip/MTTouchAndFaceID/blob/master/iPhone_1.png)
![alt text](https://github.com/manekdilip/MTTouchAndFaceID/blob/master/iPhone_2.png)
![alt text](https://github.com/manekdilip/MTTouchAndFaceID/blob/master/iPhone_3.png)

## Face ID Screenshot

![alt text](https://github.com/manekdilip/MTTouchAndFaceID/blob/master/iPhoneX-FaceId.gif)
![alt text](https://github.com/manekdilip/MTTouchAndFaceID/blob/master/iPhoneX_1.png)
![alt text](https://github.com/manekdilip/MTTouchAndFaceID/blob/master/iPhoneX_2.png)
![alt text](https://github.com/manekdilip/MTTouchAndFaceID/blob/master/iPhoneX_3.png)

## How to use

## Step-1: Just drag and drop MTFingerPrint.swift into your project folder.

## Step-2: Local Authentication Framework
    Select Project -> Targets -> Linked Frameworks and Libraries -> Add LocalAuthentication.framework

## Step-3: Add following code into viewDidLoad method of view-controller file where you want to add authentication.
    MTFingerPrint.sharedInstance.authenticationWithTouchID()
    MTFingerPrint.sharedInstance.delegate = self

## Step-4: Add following delegate method into your view-controller file

		extension yourViewControllerName : FingerPrintDelegate {
    
        func fingPrintSuccess() {

          if DeviceType.IS_IPHONE_X {

            DispatchQueue.main.async {
              print("Face ID is verified.")
            }

          } else {
            DispatchQueue.main.async {
              print("Touch ID is verified.")
            }
        }
    	}
    					
      func fingerPrintFailed() {

        if DeviceType.IS_IPHONE_X {

            DispatchQueue.main.async {
              print("Face ID is not verified.")
            }
         } else {
            DispatchQueue.main.async {
              print("Touch ID is not verified.")
            }
        }
      }

      func fingerPrintNotAvailable() {

        if DeviceType.IS_IPHONE_X {

          //self.faceSettingAlert()

        } else {

          //self.fingSettingAlert()

        }
      }
