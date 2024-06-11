# Deployment to Google Cloud Platform

This file covers the neccesary documentation for the deployment to Google Cloud Services.

## Google Cloud Platform Configuration

These are the instructions you have to do on the Google Cloud PLatform in order to have you rails application working correctly.

1. Create a new project

2. You have to add a credit card because some Google servicios required a credit card.

3. Enable Secret Manager service

4. Enable Artifact Registry service

5. Enable Cloud SQL API

6. Enable Cloud Run API

7. Create a Docker repository on the Artifact Registry service.

8. Create a custom role and name it as you want (this role is for the cloud deployment) and assign the following permissions:

  - iam.serviceAccounts.actAs
  - run.services.create
  - run.services.get
  - run.services.update
  - run.services.delete
  - run.services.getIamPolicy
  - run.services.setIamPolicy

9. Create a custom role and name it as you want (this role is for publishing images) and assign the following permissions:

  - artifactRegistry.repositories.downloadArtifacts
  - artifactRegistry.repositories.uploadArtifacts

10. Create a custom role and name it as you want (this role is for getting the secrets) and assign the following permissions:

  - secretmanager.versions.access

11. Create a custom role and name it as you want (this role is for runing operations) and assign the following permissions:

  - run.operations.get

12. Create a service account and assign these 3 custom roles and the Cloud SQL Admin role.

13. Create a workload identity federation with the following configuration:

  - my-workload-pool
  - OIDC
    - GitHub
    - https://token.actions.githubusercontent.com
  - Default audience
  - google.subject <=> assertion.actor
  - attribute.actor <=> assertion.sub
  - attribute.repository <=> assertion.repository

14. Install gcloud in the terminal

15. Authenticated gcloud with your terminal: `gcloud auth login`

16. Select the project you want to use in the terminal

17. Copy and paste the following command in your terminal. Change the options according to your own configuration.

```bash
gcloud iam service-accounts add-iam-policy-binding "paqueteria-martinez@paqueteria-martinez-ids.iam.gserviceaccount.com" --project="paqueteria-martinez-ids" --role="roles/iam.workloadIdentityUser" --member="principalSet://iam.googleapis.com/projects/850695705631/locations/global/workloadIdentityPools/paqueteria-martinez-pool/attribute.repository/Jorge-Ortiz-Mata/paqueteria-martinez"
```

18. Add your secrets on the Secret Manager service and the master key.

19. Update your workflows with your service account and the workload identity pool.

20. Uncomment the **on:** attributes and make a push to main

21. Wait until the services are ready

And that's all. If you encountered errors on the installation process, feel free to reach any of the support team by email: ortiz.mata.jorge@gmail.com
