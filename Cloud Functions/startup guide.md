# Cloud Functions
## write a Cloud Function
To create a cloud function in a GCP (Google Cloud Project)

you have to create a service in Cloud Run.

Step 1:

First, go to Google Cloud Console, then select the GCP you want to write.

<img width="1900" height="871" alt="image" src="https://github.com/user-attachments/assets/faf92663-62cf-460e-a97a-caecb6eceadc" />

Step 2:

Then search `Cloud Functions` in the search bar at top.

In marketplace, click the item `Cloud Functions`

<img width="1919" height="1031" alt="image" src="https://github.com/user-attachments/assets/0bbfb39a-cfa4-4529-a303-557697c23926" />

Step 3:

Then click `Go to Cloud Functions` button (blue button with white text)

<img width="1919" height="1054" alt="image" src="https://github.com/user-attachments/assets/0e490db0-24f7-4e97-a0f5-ec87905265ec" />

Step 4: 

Then click `Write a function` button 

<img width="1891" height="753" alt="image" src="https://github.com/user-attachments/assets/e1f52dab-a84b-420a-b0a5-64168c34f832" />

Step 5:

Then it will redirect the page with title `Create Service`,

In this page, fill in the form and click `Create` button (blue button with white text at the bottom of the panel) to submit the form.

The red highlighted boxes and the yellow ones on the following figures emphasize on important things that one has to pay attention to.

I will discuss them.

> [!IMPORTANT]
> To understand its quota for free use, please look at the `Pricing summary` section (in the yellow highlighted box) in the following figure.

<img width="1904" height="1034" alt="image" src="https://github.com/user-attachments/assets/66aad1a9-689d-49ce-880e-70c044f17c19" />

1. 

The first you thing you need to pay attention to is to determine how to create a Cloud Function.

+ If you use existing container image, please select `Deploy one revision from an existing container image`.
+ If you perform Git control with GitHub, please select `Continuously deploy from a repository (source or function)`
+ Use an inline editor to create a function  

2. The second thing you need to to pay attention to is to specify the source and the how to build the Cloud Function.

In the following figure, since I want to maintain the Cloud Function with Git on remote GitHub repo, I select `Continuously deploy from a repository (source or function)` and `Cloud Build` radio button.

<img width="1904" height="1034" alt="image" src="https://github.com/user-attachments/assets/66aad1a9-689d-49ce-880e-70c044f17c19" />

When selecting `Continuously deploy from a repository (source or function)`, these following radio buttons and `Set up Cloud Build` button are shown.

+ `Cloud Build`: select if you want the Cloud Function is compiled using Cloud Buildpacks. It is only available for Cloud Function that will be deployed to remote GitHub repo.
+ `Developer Connect`:  It is available for Cloud Function that will be deployed to remote GitHub repo, remote GitHub repo, and remote Bitbucket repo.

After I select `Cloud Build`, I click `Set up Cloud Build`, then it open a panel at the side of the page with title `Set up Cloud Build`.

In the first step -- `Source Repository`, please select the `Repository Provider` (such as GitHub) and `Repository`.

> [!IMPORTANT]
> In the first time the Cloud Run does not have authory to connect with GitHub.
>
> If it does NOT have authory, then, in below `Repository Provider` dropdown list, you will see an error saying like `GitHub is NOT authorized`,
>
> please click `Authorize` button.

> [!IMPORTANT]
> Similarly, in the first time, the API service is NOT enabled so that it can't find available repos
>
> If the API service is NOT enabled, then, in below `Repository Provider` dropdown list, you will see a warning saying like `API is not enabled`,
> 
> please click `Enable` button.

> [!IMPORTANT]
> After enabling API, it might not be able to find the connected repo,
>
> please click the hyperlink with text `Manage connected repositories` and follow the instructions.

Secondly, read the policy carefully once and tick it. 

<img width="1896" height="954" alt="image" src="https://github.com/user-attachments/assets/05e210d8-535b-4775-b9c8-908a98c20e2b" />

Then click Next to advance to next step -- `Build configuration`

In the second step -- `Build configuration`,

please specify a branch using regex and select `Build type`.

After that please click `Save` button (blue button with white text)

<img width="612" height="570" alt="image" src="https://github.com/user-attachments/assets/d8b9d94c-d186-47a0-8b33-7dfa0bcd0f12" />

3. The third thing you need to pay attention to is abount the containers settings, networking settings, security settings.

About container settings, please specify the container port number and remember it.

It will be used when you write `Dockerfile`.

Then edit your container name

> [!IMPORTANT]
> After saving the edit, it will schedule that the container will be created after finishing creating the service rather than immediately create a container.
>
> Thus, the `container name` displayed on the page will be NOT be re-render.
  
<img width="654" height="653" alt="image" src="https://github.com/user-attachments/assets/86c5bc9d-40ef-408d-827e-88e0be11f07c" />

About networking settings,

<img width="329" height="183" alt="image" src="https://github.com/user-attachments/assets/cb7df017-5bcd-4e08-b6bc-758fa630cc29" />

About security settings,

you need to select service account that this service will use, in the `Service account` dropdown list.

<img width="660" height="404" alt="image" src="https://github.com/user-attachments/assets/c28a6188-bc20-48f2-9aa8-af7c67a0b9cd" />

4. The last thing you need to pay attention to is to fill a descriptive name as the service name.

5. Then you can click `Create` button to create the service.

<img width="1904" height="1034" alt="image" src="https://github.com/user-attachments/assets/66aad1a9-689d-49ce-880e-70c044f17c19" />
