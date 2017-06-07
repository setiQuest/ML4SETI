### Using tutorial notebooks in DSX

1. Direct your browser to https://datascience.ibm.com/ and log in (or sign up)

   ![Sign-in to DSX](../img/dsx/clone_notebook/sign_in_to_dsx.png)

2. Select **Projects** > **View All Projects**

   ![Open project list](../img/dsx/clone_notebook/open_project_list.png)

3. Click **create project**. The New Project wizard opens.

   ![Create project](../img/dsx/clone_notebook/create_project.png)

4. Enter a project name, select **DSX-Spark** as _Spark Service_, **Object Storage** as _Storage Type_ and **DSX-ObjectStorage** as _Object Storage Instance_. Click **Create**.

4. This new project is empty by default. Create a new notebook by clicking **add notebooks** in the project _Overview_ tab.

   ![Add notebook](../img/dsx/clone_notebook/add_notebook.png)

5. Select **From URL**, type in a notebook _name_, enter the _URL_ of the notebook you want to load and select **DSX-Spark** as _Spark Service_. Click **Create Notebook**.

   ![Create notebook](../img/dsx/clone_notebook/add_notebook_wizard.png)

6. The notebook opens and a Spark kernel is automatically started.

   ![Add notebook](../img/dsx/clone_notebook/edit_notebook.png)

   >  In Data Science Experience each notebook is associated with a kernel. This kernel will remain running until you explicitly shut down the kernel. 
   
### Saving the notebook

Notebooks are perioodically saved. However, to avoid loosing any changes manually save changes by selecting **File** > **Save**.

   ![Save notebook](../img/dsx/save_notebook.png)

### Checking the Spark kernel status

You can view the Spark kernel status in the and the project overview.

   ![Check kernel status](../img/dsx/check_kernel_status.png)

### Stopping the Spark kernel

* You can stop a running kernel in the project overview by selecting **…** > **Stop Kernel**.

   ![Stop kernel](../img/dsx/stop_kernel.png)

* To stop a kernel while the notebook is open select **File** > **Stop Kernel**.

   ![Stop kernel in notebook](../img/dsx/stop_kernel_in_notebook.png)

### Restarting the Spark kernel

To restart a kernel while the notebook is open select **Kernel** > **Restart**.

   ![Restart kernel](../img/dsx/restart_kernel_in_notebook.png)

### Re-opening a notebook

To re-open a notebook open the project overview and click the pencil icon.

   ![Re-open notebook](../img/dsx/open_edit.png)
