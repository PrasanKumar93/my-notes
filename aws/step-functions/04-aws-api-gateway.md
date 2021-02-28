## API gate way

- Search "API gateway" service in search box

![API Gateway](./images/aws/api-01.png)

- Click on **Build** in REST API (complete control)

- Create API page
  ![Create API](./images/aws/api-02.png)

  ![Fill API form](./images/aws/api-03.png)

  ![API form](./images/aws/api-04.png)

  ![API form](./images/aws/api-05.png)

  ![API form](./images/aws/api-06.png)

### TO fill execution role IAM

- open AWS console in new tab & search for "IAM" service in search box

![IAM](./images/aws/api-07.png)

- Click on Roles in left side bar & 'Create role' button on screen

![IAM](./images/aws/api-08.png)

- Select 'AWS Service' type, 'API gateway' use case & click on Next

![IAM](./images/aws/api-09.png)

- Click Next

![IAM](./images/aws/api-10.png)

- Click Next

![IAM](./images/aws/api-11.png)

- Fill role details & click 'Create role'
  ![IAM](./images/aws/api-12.png)
  ![IAM](./images/aws/api-13.png)

- Click on newly created role
  ![IAM](./images/aws/api-14.png)

- IN permission section, click on attach policy.
  search for step function, select 'AWSStepFunctionsFullAccess' & click on 'Attach Policy'
  ![IAM](./images/aws/api-15.png)

- Finally copy the role ARN
  ![IAM](./images/aws/api-16.png)

### API gateway continued

- Fill the role ARN & click on save
  ![API form](./images/aws/api-17.png)

- CLick on test
  ![API form](./images/aws/api-18.png)

  ![API form](./images/aws/api-19.png)

  ![API form](./images/aws/api-20.png)

  ![API form](./images/aws/api-21.png)

### Deploy API to test remote

- In actions, choose deploy API
  ![API Test](./images/aws/api-22.png)
  ![API Test](./images/aws/api-23.png)

- Copy the invoke URL  
  ![API Test](./images/aws/api-24.png)

- Test URL in postman
  ![API Test](./images/aws/api-25.png)

## Links

- [API gateway step functions docs](https://docs.aws.amazon.com/step-functions/latest/dg/tutorial-api-gateway.html)
