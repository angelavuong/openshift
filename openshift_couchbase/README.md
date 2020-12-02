# Openshift 4 with Couchbase


## Topics:

### How to install Couchbase on Openshift 4
1. Create a namespace for your Couchbase installation (e.g. couchbase)

    ![image1](https://github.com/angelavuong/openshift_couchbase/blob/main/images/image1.png)


2. Install the Couchbase operator from the Operator Hub (ensure you deploy to a specific namespace, not all namespaces).

    ![image2](https://github.com/angelavuong/openshift_couchbase/blob/main/images/image2.png)

    ![image3](https://github.com/angelavuong/openshift_couchbase/blob/main/images/image3.png)

    ![image4](https://github.com/angelavuong/openshift_couchbase/blob/main/images/image4.png)

    ![image5](https://github.com/angelavuong/openshift_couchbase/blob/main/images/image5.png)

3. Verify that the Couchbase operator pod was created.

    ![image6](https://github.com/angelavuong/openshift_couchbase/blob/main/images/image6.png)

4. Create a secret for the deployment (secret.yaml).

    ![image7](https://github.com/angelavuong/openshift_couchbase/blob/main/images/image7.png)

    ![image8](https://github.com/angelavuong/openshift_couchbase/blob/main/images/image8.png)

5. Go back to your Couchbase operator and create a Couchbase Cluster (couchbase-cluster.yaml).

6. Wait and verify all your resources are created.

    ![image9](https://github.com/angelavuong/openshift_couchbase/blob/main/images/image9.png)

7. Create a route for your app deployment.

    ![image10](https://github.com/angelavuong/openshift_couchbase/blob/main/images/image10.png)

8. Verify you can reach the external route URL provided.

    ![image11](https://github.com/angelavuong/openshift_couchbase/blob/main/images/image11.png)

    NOTE:
    Default login should be user: ```Administrator``` / pass: ```password```

**Resources:**

1) [Fully Configured Couchbase on Red Hat OpenShift Under Five Minutes](https://blog.couchbase.com/fully-configured-couchbase-on-red-hat-openshift-under-five-minutes/)

2) [Installing on Openshift - Couchbase Documentation](https://docs.couchbase.com/operator/1.1/install-openshift.html)

3) [Couchbase on Openshift in Action](https://blog.couchbase.com/couchbase-on-openshift-in-action/)
