# Cloud Functions
## write a Cloud Function
To create a cloud function in a GCP (Google Cloud Project)

you have to create a service in Cloud Run.

### Part 1 -- create a service in Cloud Run page.

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

1. The first you thing you need to pay attention to is to determine how to create a Cloud Function.

+ If you use existing container image, please select `Deploy one revision from an existing container image`.
+ If you perform Git control with GitHub, please select `Continuously deploy from a repository (source or function)`
+ Use an inline editor to create a function  

2. Case 1: If you specify `Continuously deploy from a repository (source or function)` radio button,

<img width="109" height="83" alt="image" src="https://github.com/user-attachments/assets/83c0ab8a-0911-4c8d-aafc-11e8c00b9b68" />

then the second thing you need to to pay attention to is to specify the source and the how to build the Cloud Function.

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

Additionally you need to pay attention to configure the containers settings, networking settings, security settings.

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

Case 2: If you specify `Use an inline editor to create a function` radio button

<img width="107" height="76" alt="image" src="https://github.com/user-attachments/assets/939c56ff-6e90-43da-9199-60a2cb345366" />

Then the second thing you need to pay attention to is to specify the runtime environment.

<img width="324" height="53" alt="image" src="https://github.com/user-attachments/assets/9e29426d-4368-401c-85e4-f0ab886058bf" />

Also you might want to add a trigger (or you can add it later (after creating the service)) 

The trigger will be triggered only if specified event is met.

In the trigger, you can

  + specify which event will trigger the trigger by specifying the event type <img width="221" height="26" alt="image" src="https://github.com/user-attachments/assets/c49111e9-0485-4ba5-9473-88911979d4bf" />

  + specify the region that the operation about the trigger will be used at <img width="212" height="23" alt="image" src="https://github.com/user-attachments/assets/03023790-4d59-43e6-91f1-f573bc32fca6" />

  + specify the service account, the account will be used for this service <img width="214" height="26" alt="image" src="https://github.com/user-attachments/assets/0a7afdfe-2771-4963-a1ad-28363d680458" />

  + (optional) add labels to organize your project <img width="215" height="83" alt="image" src="https://github.com/user-attachments/assets/4d0ff1b1-887f-4b3c-a76e-e049c8367c95" />

  + and so on.
    
> [!WARNING]
> The region you specified in the trigger takes higher precedence than the region you specified in the configure section <img width="666" height="141" alt="image" src="https://github.com/user-attachments/assets/3fc99b1f-f91e-49c7-ad4d-66c27772faf7" />

After filling in, click `Save trigger` button (blue button with white text) to save it.

<img width="474" height="759" alt="image" src="https://github.com/user-attachments/assets/b69c151f-32dd-491f-a08f-07baa77beacf" />

The you will see a trigger like this

<img width="213" height="154" alt="image" src="https://github.com/user-attachments/assets/fa8909b2-dcff-43eb-8196-ad3b142b2e08" />

3. The third thing you need to pay attention to is to fill a descriptive name as the service name.

<img width="323" height="138" alt="image" src="https://github.com/user-attachments/assets/0ff9d6f5-4261-4d35-848c-919f53d77386" />

4. The fourth thing you need to pay attention to is to set a region.

The service will be used by the compute engine located at the specified region.

> [!IMPORTANT]
> The region you specified relates to the tier level which relates to billing account.
>
> Please watch out it and pay attention to `Pricing summary` to save your cost.
>
> Also, I recommend to select region with tier 1 for beginner,
>
> since tier 1 is free (if you don't consume up more than the available free qutoa) and
>
> usually fits for personnal use (such as just practicing CI/CD) within its free quota. 

<img width="323" height="138" alt="image" src="https://github.com/user-attachments/assets/0ff9d6f5-4261-4d35-848c-919f53d77386" />

5. The fifth thing you need to pay attention to is to the billing method.

I highly recommended you to select `Request-based`.

If `Request-based` is selected, 

then, iff when processing requests, the quota is consumed and it is charged since CPU is limited outside of requests.

Otherwise, the CPU is always consumed and thus the free quota is always consume and consequently you might receive a billing account that spends lots of cash.

<img width="262" height="59" alt="image" src="https://github.com/user-attachments/assets/a04edc9d-c12b-4590-af02-19bd4f41c54f" />

6. The sixth thing you need to pay attention to is to set the execution environment.

I highly recommend to execute it with the newest generation (now it is, Second generation) for better compatibility and faster performance.

> [!IMPORTANT]
> It auto-fills `Default` radio button by default, please select different radio if needed.

<img width="309" height="99" alt="image" src="https://github.com/user-attachments/assets/2985c8b2-2dcd-4c5d-86f8-c1ba5f096607" />

7. The seventh thing you need to pay attention to is to set the request timeout and maximam available concurrent requests. 

> [!IMPORTANT]
> The `Requests timeout` field takes one second as unit.

<img width="644" height="176" alt="image" src="https://github.com/user-attachments/assets/ab3b7139-708a-4284-a94e-6e29e7a430ef" />

8. Lastly you can click `Create` button (at the bottom of the panel) to create the service.

<img width="133" height="86" alt="image" src="https://github.com/user-attachments/assets/95d2e2b6-ccae-4629-b02b-b6d7db87bc18" />

### Part 2 -- Writing a function
#### Case 1: deploy on repo with git
If you deploy on repo with git, and the build type is set to `Dockerfile` (see 2th point you need to pay attention to), 

<img width="307" height="283" alt="image" src="https://github.com/user-attachments/assets/0dec583d-a5da-4d19-b2de-4771d880bb65" />

then you have to write your logic into the file then push it.

> [!IMPORTANT]
> The file path of the file you pushed MUST correspond to the location specified in `Source location` field
>
> since it will use this file when the event is triggered. 
