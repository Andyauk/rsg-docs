# Windows Intallation

## **Generate a Key**

Goto [Keymaster](https://keymaster.fivem.net/) login and generate a key for later use.

## **Download the server**

1. Go to the [Windows server build listing](https://runtime.fivem.net/artifacts/fivem/build\_server\_windows/master/) ('artifacts' listing, as in 'build artifacts').
2. Download the latest recommended build.

<div align="left">

<figure><img src="../.gitbook/assets/windows-step-2.png" alt=""><figcaption></figcaption></figure>

</div>

3. Open the `server.7z` you just downloaded. Use any third-party archiving tool (such as [7-Zip](https://www.7-zip.org/download.html) or [WinRAR](https://www.rarlab.com/download.htm)) to open the `.7z` file.
4. Create the following folder structure in your `C:\` drive
   * create folder `C:\redm`
   * create folder `C:\redm\server-data`
   * create folder `C:\redm\server-files`
5. Extract the filesfrom `server.7z` to `C:\redm\server-data`
6. Open the folder you just extracted it to. It should look a little like this:

<div align="left">

<figure><img src="../.gitbook/assets/windows-step-5.png" alt=""><figcaption></figcaption></figure>

</div>

## **Start the server**

1. Double click `FXServer.exe`

<div align="left">

<figure><img src="../.gitbook/assets/windows-step2-1.png" alt=""><figcaption></figcaption></figure>

</div>

2. This site should open in your browser, make sure a PIN is filled and click `Link Account`.

<div align="left">

<figure><img src="../.gitbook/assets/windows-step2-2.png" alt=""><figcaption></figcaption></figure>

</div>

3. Log in to your account on [Cfx.re](https://forum.cfx.re/) in this tab and then click `CONTINUE`

<div align="left">

<figure><img src="../.gitbook/assets/Screenshot 2023-10-06 180807.png" alt=""><figcaption></figcaption></figure>

</div>

4. Set a password to log in to your server's admin page.

<div align="left">

<figure><img src="../.gitbook/assets/Screenshot 2023-10-06 181029.png" alt=""><figcaption></figcaption></figure>

</div>

5. Click 'Next'.

<div align="left">

<figure><img src="../.gitbook/assets/Screenshot 2023-10-06 181229.png" alt=""><figcaption></figcaption></figure>

</div>

6. Type a name for your server and click 'Next'.
7. Select 'Remote URL Template'

<div align="left">

<figure><img src="../.gitbook/assets/Screenshot 2023-10-06 181455.png" alt=""><figcaption></figcaption></figure>

</div>

8. Enter the following URL into the box and click `Next`

{% embed url="https://raw.githubusercontent.com/Rexshack-RedM/txAdminRecipe/main/rsgcore.yaml" %}

<figure><img src="../.gitbook/assets/Screenshot 2023-10-06 181634.png" alt=""><figcaption></figcaption></figure>

9. Click `Change Path` and enter the following file path `C:\redm\server-data` and click `Save`

<figure><img src="../.gitbook/assets/Screenshot 2023-10-06 182042.png" alt=""><figcaption></figcaption></figure>

10. Click `Go to Recipe Deployer`

<div align="left">

<figure><img src="../.gitbook/assets/Screenshot 2023-10-06 182209.png" alt=""><figcaption></figcaption></figure>

</div>

11. Review the recipe and click `Next`

<div align="left">

<figure><img src="../.gitbook/assets/Screenshot 2023-10-06 182409.png" alt=""><figcaption></figcaption></figure>

</div>

12. Enter the key you just made on the [Keymaster](https://keymaster.fivem.net/) and then select `Run Recipe`

<div align="left">

<figure><img src="../.gitbook/assets/Screenshot 2023-10-06 182728.png" alt=""><figcaption></figcaption></figure>

</div>

13. Wait for the recipe to finish and click `Next`

<div align="left">

<figure><img src="../.gitbook/assets/Screenshot 2023-10-06 183723.png" alt=""><figcaption></figcaption></figure>

</div>

14. Click `Save & Run Server`

<div align="left">

<figure><img src="../.gitbook/assets/Screenshot 2023-10-06 183854.png" alt=""><figcaption></figcaption></figure>

</div>

## **RSG RedM Server Build**

Watch the below video of me Installing a RSG RedM Server via txAdmin

**Recipe** : [https://raw.githubusercontent.com/Rexshack-RedM/txAdminRecipe/main/rsgcore.yaml](https://raw.githubusercontent.com/Rexshack-RedM/txAdminRecipe/main/rsgcore.yaml)

{% embed url="https://www.youtube.com/watch?v=2zFfizkDfoc" %}

## **Addtional Requirements:**

* xampp : [https://www.apachefriends.org/](https://www.apachefriends.org/) or MariaDB [https://mariadb.org/download/](https://mariadb.org/download/)​
* artifacts : [https://runtime.fivem.net/artifacts/fivem/build\_server\_windows/master/](https://runtime.fivem.net/artifacts/fivem/build\_server\_windows/master/)
* redm : [https://redm.net/](https://redm.net/)​

## **Setup Ports**

{% embed url="https://www.youtube.com/watch?v=Smva0MA_g5o" %}

this is for fivem but its also the same for redm servers
