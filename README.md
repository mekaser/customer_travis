# Appdome Android Fuse&Sign action
Appdome's Build-2Secure GitHub Action is an out-of-the-box GitHub CI/CD integration, making it easy for mobile developers to automate the build, signing, and certification of security, anti-fraud, and other protections in Android & iOS apps in GitHub CI/CD pipelines. No code and no SDKs are required.

The purpose of Appdome's Build-2Secure Action for GitHub is to streamline and accelerate cyber and anti-fraud delivery in CI/CD pipelines. To do this, the Build-2Secure Action for GitHub automates three important steps in delivering more secure mobile applications to your users fast: (1) building app-level protections into mobile apps, (2) code signing the protected mobile app, and (3) certifying the security of each protected mobile app. The Appdome Build-2Secure Action for GitHub can be used to deliver Certified Secure™ mobile app security, anti-fraud, anti-malware, mobile anti-bot, and other cyber defense updates to mobile apps on the Appdome Cyber Defense Automation Platform. Use this Action for GitHub as a stand-alone DevSecOps integration or in combination with other DevSecOps integrations in your CI/CD pipeline.
# config.yaml 
# Usage 
config.yml :
### Android - AUTO_SIGNING
```yaml
# config.yaml
platform: "ANDROID"
appdome_build:
  APP_FILE: "https://appdome-automation-vanilla-apps.s3.amazonaws.com/Thomas/PipelineFiles/Apps/FileFinder.aab?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAUMYEOMD5JGE4UVGR%2F20240807%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Date=20240807T095002Z&X-Amz-Expires=36000&X-Amz-SignedHeaders=host&X-Amz-Signature=662b3b313e0b9a1cb041ec2181fa608c9f3f93477574a249d919ac2e013caded"
  APPDOME_API_TOKEN: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoiYWQ2Yzk4MzAtMTY5OC0xMWVmLWI2NDktMzM3Y2U1NzAwNDY3Iiwic2FsdCI6IjRmMjBjMTRjLWU1MWItNDQ3YS1hMjBjLTNmY2FiNGIxODFlYSJ9.AI5soWJrClObNzD1T0yy_hLWVfLGyam08fhQm5QT4qs"
  SIGN_OPTIONS: "SIGN_ON_APPDOME"
  FUSION_SET_ID: "37015ab0-226d-11ef-a76e-97c41ade4d80"
  SECOND_OUTPUT: "true"
  GOOGLE_PLAY_SIGNING: "true"
  SIGN_FINGERPRINT: "8DF593C1B6EAA6EADADCE36831FE82B08CAC8D74"
  BUILD_TO_TEST: "None"
  TEAM_ID: "None"
  APPDOME_SERVER_BASE_URL: "https://qamaster.dev.appdome.com/"
  OUTPUT_APP_NAME: "myapp_SIGN_ON_APPDOME.aab"
  KEYSTORE_FILE: "./files/appdome(5).keystore"
  KEYSTORE_PASSWORD: "appdome"
  KEYSTORE_ALIAS: "appdome"
  KEYSTORE_KEY_PASSWORD: "appdome"
  BUILD_WITH_LOGS: "true"
```



### Android - PRIVATE_SIGNING
```yaml
platform: "ANDROID"
appdome_build:
  APPDOME_API_TOKEN: "env_var.APPDOME_API_TOKEN"
  TEAM_ID: "None"
  APP_FILE: "# none_protected_application can be pass as path/on/repository OR https://download_link"
  FUSION_SET_ID: "Appdome Fusion Set_Id Android"
  SIGN_OPTIONS: "PRIVATE_SIGNING"
  GOOGLE_PLAY_SIGNING: "true" #- Optional
  BUILD_TO_TEST: ' "lambdatest" | "bitbar" | "browserstack" | "saucelabs" or "None" - Optional - since version 1.1.0'
  SIGN_FINGERPRINT: "env_var.SIGN_FINGERPRINT" # -Mandatory if SIGN_OPTIONS is PRIVATE_SIGNING or AUTO_DEV_SIGNING
  APPDOME_SERVER_BASE_URL: "https://qamaster.dev.appdome.com/"
  OUTPUT_APP_NAME: "myapp_PRIVATE_SIGNING.aab" # -Optional, will also apply for second output universal apk
  SECOND_OUTPUT: "true" # -Optional
  BUILD_WITH_LOGS: "true" # -Optional
```

### Android - AUTO_DEV_SIGNING
```yaml
# config.yaml
platform: "ANDROID"
appdome_build:
  APPDOME_API_TOKEN: "env_var.APPDOME_API_TOKEN"
  TEAM_ID: "Your team id in appdome"
  APP_FILE: "# none_protected_application can be pass as path/on/repository OR https://download_link"
  FUSION_SET_ID: "Appdome Fusion Set_Id Android"
  SIGN_OPTIONS: "AUTO_DEV_SIGNING"
  GOOGLE_PLAY_SIGNING: "true" #- Optional
  BUILD_TO_TEST: ' "lambdatest" | "bitbar" | "browserstack" | "saucelabs" or "None" - Optional - since version 1.1.0'
  SIGN_FINGERPRINT: "env_var.SIGN_FINGERPRINT" # -Mandatory if SIGN_OPTIONS is PRIVATE_SIGNING or AUTO_DEV_SIGNING
  APPDOME_SERVER_BASE_URL: "https://qamaster.dev.appdome.com/"
  OUTPUT_APP_NAME: "Output_app_name" #- Optional, this also supports a full path.
  BUILD_WITH_LOGS: "true" # -Optional
```

### iOS - AUTO_SIGNING
```yaml
# config.yaml
platform: "IOS"
appdome_build:
  APPDOME_API_TOKEN: "env_var.APPDOME_API_TOKEN"
  TEAM_ID: "None"
  APP_FILE: "# none_protected_application can be pass as path/on/repository OR https://download_link"
  FUSION_SET_ID: "env_var.FUSION_SET_ID"
  SIGN_OPTIONS: "SIGN_ON_APPDOME"
  GOOGLE_PLAY_SIGNING: "true"
  BUILD_TO_TEST: ' "lambdatest" | "bitbar" | "browserstack" | "saucelabs" or "None" - Optional - since version 1.1.0'
  APPDOME_SERVER_BASE_URL: "https://qamaster.dev.appdome.com/"
  OUTPUT_APP_NAME: "myapp_SIGN_ON_APPDOME.ipa"
  BUILD_WITH_LOGS: "true"
  CERTIFICATE_FILE: ' "./files/<CERTIFICATE_FILE name>" ...
                   OR “<https_download_link>” ...
                   OR "env_var.CERTIFICATE_FILE"'
  CERTIFICATE_PASSWORD: "env_var.CERTIFICATE_PASSWORD"
  MOBILE_PROVISION_PROFILE_FILE: ' "./files/<MOBILE_PROVISION_PROFILE_FILE name>" ...
                                OR “<https_download_link>” ...
                                OR "env_var.MOBILE_PROVISION_PROFILE_FILE"'
  ENTITLEMENTS_FILE: ' "./files/<ENTITLEMENTS_FILE name>" ...
                    OR “<https_download_link>” ...
                    OR env_var.ENTITLEMENTS_FILE'
```

### iOS - PRIVATE_SIGNING
```yaml
# config.yaml
platform: "IOS"
appdome_build:
  APPDOME_API_TOKEN: "env_var.APPDOME_API_TOKEN"
  TEAM_ID: "Your team id in appdome"
  APP_FILE: "# none_protected_application can be pass as path/on/repository OR https://download_link"
  FUSION_SET_ID: "Appdome Fusion Set_Id Android"
  SIGN_OPTIONS: "PRIVATE_SIGNING" #
  BUILD_TO_TEST: ' "lambdatest" | "bitbar" | "browserstack" | "saucelabs" or "None" - Optional - since version 1.1.0'
  APPDOME_SERVER_BASE_URL: "https://qamaster.dev.appdome.com/"
  OUTPUT_APP_NAME: "Output_app_name" #- Optional, this also supports a full path.
  BUILD_WITH_LOGS: "true" # -Optional
  MOBILE_PROVISION_PROFILE_FILE: ' "./files/<MOBILE_PROVISION_PROFILE_FILE name>" ...
                                OR “<https_download_link>” ...
                                OR "env_var.MOBILE_PROVISION_PROFILE_FILE"'
  ENTITLEMENTS_FILE: ' "./files/<ENTITLEMENTS_FILE name>" ...
                    OR “<https_download_link>” ...
                    OR env_var.ENTITLEMENTS_FILE'
```

### iOS - AUTO_DEV_SIGNING
```yaml
# config.yaml
platform: "IOS"
appdome_build:
  APPDOME_API_TOKEN: "env_var.APPDOME_API_TOKEN"
  TEAM_ID: "Your team id in appdome"
  APP_FILE: "# none_protected_application can be pass as path/on/repository OR https://download_link"
  FUSION_SET_ID: "Appdome Fusion Set_Id Android"
  SIGN_OPTIONS: "PRIVATE_SIGNING" #
  BUILD_TO_TEST: ' "lambdatest" | "bitbar" | "browserstack" | "saucelabs" or "None" - Optional - since version 1.1.0'
  APPDOME_SERVER_BASE_URL: "https://qamaster.dev.appdome.com/"
  OUTPUT_APP_NAME: "Output_app_name" #- Optional, this also supports a full path.
  BUILD_WITH_LOGS: "true" # -Optional
  MOBILE_PROVISION_PROFILE_FILE: ' "./files/<MOBILE_PROVISION_PROFILE_FILE name>" ...
                                OR “<https_download_link>” ...
                                OR "env_var.MOBILE_PROVISION_PROFILE_FILE"'
  ENTITLEMENTS_FILE: ' "./files/<ENTITLEMENTS_FILE name>" ...
                    OR “<https_download_link>” ...
                    OR env_var.ENTITLEMENTS_FILE'
```