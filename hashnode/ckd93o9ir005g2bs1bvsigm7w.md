## Multi-Factor Authentication

# Internet Security

With online accounts and services becoming more and more prevalent, the necessity of internet security is increasingly vital. Many people, despite recommendations to the contrary, use the same password for multiple sites - exposing themselves to vulnerability without knowing it. Password managers are an option for keeping track of your different passwords for each online account, though the safety of such methods is questionable. For the best security, I recommend (and use) multi-factor authentication.

## What IS multi-factor authentication?

Multi-factor authentication (or MFA) is an authentication method that requires additional steps to verify your credentials - *beyond* just a username and password. There are three popular methods for MFA, and I will go in to a little detail about each:
1. SMS Verification
2. Authenticator Applications
3. Physical Security Key

The core principle of MFA is that you require two things to access your account: Something you *know*, such as your password, and something you *have*, such as your mobile phone. 

## SMS Verification

SMS (short message servce) Verification systems generate a one-time passcode (OTP) that is sent to your mobile phone number via a text message. The website or application then prompts you to enter that OTP - upon validating that your input matches the token the system generated, it completes the authentication and grants access to your account. 

SMS Verification is the easiest to set up, but comes with some downfalls. The most notable concern with SMS verification is that it requires your device to have an active cellular connection. Generally, this should not be an issue - but say you are at a hotel out of town, and need to check your email. You log in on the hotel computer, and the MFA prompts you for the OTP. Your phone doesn't have cell service, and even though you have a Wi-Fi connection you cannot receive SMS messages. Now you are unable to access your account!

Additionally, SMS verification *can* be hijacked. It is possible (and has been tested) for a malicious person to "read" your SMS data while it is in transit to your device - thereby grabbing that OTP and accessing your account fraudulently. I would argue that this is not common enough to be a concern for the standard user, but is something worth considering if you are interested in strict security practises. 

## Authenticator Applications

To alleviate the concerns with SMS verification, many websites that offer MFA options allow the use of an authenticator application (such as Google Authenticator). This application is connected to your account through a setup process on the website's interface - once connected, the authenticator application will continuously generate access tokens. When you attempt to log in to your account, the website will ask for that access token value - input the value from your authenticator application, and you are good to go! 

An authenticator application functions completely offline - meaning your mobile device does not need an Internet or cellular connection. The advantages of this setup are that you can generate the tokens from anywhere (even that hotel we talked about earlier) and a malicious person could not scrape your token from a data transmission packet. However, it is still *theoretically* possible for a fraudulent application (downloaded to your phone) to read the data in the authenticator application and provide those tokens to a malicious person. 

## Physical Security Key

Arguably the most secure MFA option of the three, a physical security key is a stand-alone unit that serves as your second level authentication. Rather than entering a code into the website prompt, a physical security key gets plugged in to the computer (usually via USB) and directly communicates with the website to complete the second level authentication. 

Physical security keys are highly hack-resistant, and would require a malicious user to obtain the key from you directly (don't lose it!). The downside is that you *have* to carry the key with you to access your accounts. If you travelled to our fictional hotel, but left your key at home, you would be unable to log in to your account. Unless...

## Backup Codes

Regardless of which method of MFA you choose, most websites will generate a set of back-up codes when you initially configure your MFA options. These codes serve as a failsafe, allowing you to access your account in the event that your MFA option is unavailable. Generally, each back-up code can only be used *once* before becoming invalid. 

When you receive the list of back-up codes, it is __vital__ that you keep them safe and secure. Often times, the website will allow you to download the codes - if you choose to do so, I strongly recommend saving them locally, and not on a cloud platform (such as Google Drive). This will make them harder for a malicious user to obtain. For an even safer option, go "off the grid" and write the codes down in a notebook or on a sheet of paper - then secure them in your house (like a safe?) and ensure no one has access to them. 

Remember: These codes *completely bypass* your MFA measures. 

## In Conclusion

Internet security is highly important, and not something to be taken lightly. Keep your passwords safe (and unique!), and set up your MFA! Of the three MFA options we have covered, I prefer the authenticator app for the balance of security and ease of use. Which option do you prefer?