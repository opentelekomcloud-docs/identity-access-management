:original_name: iam_01_0013.html

.. _iam_01_0013:

Viewing Audit Logs
==================

After you enable CTS, it records key operations performed on IAM. You can view the operation records of the last 7 days on the CTS console.

Viewing IAM Audit Logs
----------------------

#. Log in to the management console.

#. Click **Service List** in the upper part of the page and choose **Cloud Trace Service** under **Management & Deployment**.

#. In the navigation pane, choose **Trace List**.

#. Click **Filter** in the upper right corner of the trace list to set filter conditions.

   The following filters are available:

   -  **Trace Source**, **Resource Type**, and **Search By**

      -  Select a filter criteria from the drop-down list. Specifically, select **IAM** from the **Trace Source** drop-down list.
      -  If you select **Trace name** for **Search By**, select a trace name.
      -  If you select **Resource ID** for **Search By**, select or enter a resource ID.
      -  If you select **Resource name** for **Search By**, select or enter a resource name.

   -  **Operator**: Select an operator (a user rather than domain).
   -  **Trace Status**: Available options include **All trace statuses**, **normal**, **incident,** and **warning**.
   -  Specify the start time and end time for querying traces.

#. Click **Query**.

#. Expand the details of a trace, as shown in :ref:`Figure 1 <iam_01_0013__fig181771925164317>`.

   .. _iam_01_0013__fig181771925164317:

   .. figure:: /_static/images/en-us_image_0000001420274829.png
      :alt: **Figure 1** Expanding trace details

      **Figure 1** Expanding trace details

#. Click **View Trace** in the **Operation** column. In the **View Trace** dialog box as shown in :ref:`Figure 2 <iam_01_0013__fig9310171012116>`, the trace details are displayed.

   .. _iam_01_0013__fig9310171012116:

   .. figure:: /_static/images/en-us_image_0000001420034725.png
      :alt: **Figure 2** Viewing a trace

      **Figure 2** Viewing a trace
