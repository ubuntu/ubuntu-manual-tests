The goal of this test case is to check that localization support is functional during the installation, that language packs are downloaded and installed correctly from the Internet and that the input methods for either Chinese, Japanese or Korean are working. 

Boot up the image. When you see the aubergine screen with an icon at the bottom, press any key to get the menu
    Language list will appear
Use arrow keys to select 中文(简体) (Simplified Chinese), 中文(繁體) (Traditional Chinese), 日本語 (Japanese) or 한국어 (Korean) as language and press Enter
    Language list will close.
    The installer is localized from this screen onwards
Click on the Install FAMILY button
    

  * In Simplified Chinese ""安装 FAMILY""
  * In Traditional Chinese ""安裝 FAMILY""
  * In Japanese ""FAMILY をインストール""
  * In Korean ""Ubuntu 설치""


Check if your keyboard layout is correct or alter and click Continue.
    

  * In Simplified Chinese ""继续""
  * In Traditional Chinese ""繼續""
  * In Japanese ""続ける""
  * In Korean ""계속""


The 'Preparing to install FAMILY' screen is displayed, click on the Continue button
    

  * In Simplified Chinese ""继续""
  * In Traditional Chinese ""繼續""
  * In Japanese ""続ける""
  * In Korean ""계속""


    The 'Installation type' screen is displayed
On the 'Installation type' screen, select Erase disk and install Ubuntu, and click Install Now.
    

  * In Simplified Chinese ""清空并使用整个硬盘"" (Erase and use the entire disk) and ""现在安装(I)"" (Install Now)
  * In Traditional Chinese ""消除並使用整個磁碟"" (Erase and use the entire disk) and ""立刻安裝(I)"" (Install Now)
  * In Japanese ""ディスクを削除してUbuntuをインストール"" (Erase and use the entire disk) and ""インストール(I)"" (Install Now)
  * In Korean ""디스크를 지우고 Ubuntu 설치"" (Erase and use the entire disk) and ""지금 설치(I)"" (Install Now)


Select your timezone and click Continue.
    

  * In Simplified Chinese ""继续""
  * In Traditional Chinese ""繼續""
  * In Japanese ""続ける""
  * In Korean ""계속""


Input your initial user details and password. /!\ Note admin can not be used. It is a dedicated Linux User.
Tick Log in automatically and click on Continue.
    

  * In Simplified Chinese ""自动登录"" (Log in automatically) and ""继续""
  * In Traditional Chinese ""自動登入"" (Log in automatically) and ""繼續"" (Forward)
  * In Japanese ""自動的にログインする"" (Log in automatically) and ""続ける"" (Continue)
  * In Korean ""자동으로 로그인"" (Log in automatically) and ""계속"" (Forward)


Check that the installer's slides are localized.
Once the installer has finished click the Restart now button.
Remove the disc and press Enter.
Allow the machine to reboot.
Verify that your system is localized. For any language, the system has to be fully localized. /!\ Note: the translation coverage of some languages might not be complete.
Verify that the input method works correctly.
    

  * Simplified Chinese: 
    * Open dash and type gedit into the search box. Click on the editor (文本编辑器) icon.
    * Click on the keyboard icon on the top panel area and select SunPinyin as the input method to switch to.
    * Type renlei in the new gedit document, press Space, and see if it turns out to be 人类
  * Traditional Chinese: 
    * Open dash and type gedit into the search box. Click on the editor (文字编辑器) icon.
    * Click on the keyboard icon on the top panel area and select Chewing (酷音) as the input method to switch to. 
    * Type bp6xo4 in the new gedit document (or if you have a keyboard with Bopomofo, type ㄖㄣˊㄌㄟˋ), press Enter, and see if it turns out to be 人類
  * Japanese: 
    * Open dash and type gedit into the search box. Click on the editor (テキストエディター) icon.
    * Click on the keyboard icon on the notification area, select 日本語 - Anthy as the input method to switch to. 
    * Type nihon in the new gedit document, press Enter and see if it turns out to be にほん
    * Type nihon again, then press space and see if it turns out to be 日本 or 二本. Keep pressing space to cycle between the presented options, if necessary
  * Korean: 
    * Open dash and type gedit into the search box. Click on the editor (텍스트 편집기) icon.
    * Click on the keyboard icon on the notification area, select Hangul (한국어) as the input method to switch to.
    * Type gks rmf in the new gedit document and see if it turns out to be 한 글


Check that the calendar shows the regional settings correctly.
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
