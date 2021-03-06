Here are the steps to load the flights data into a Cloud SQL instance:
* In CloudShell, change to the 03_sqlstudio directory in your clone of the source code repository.
* Run the script ./create_instance.sh
* Go the GCP web console and change the root password of the Cloud SQL instance.
* Create the table by running the script ./create_table.sh. The script will prompt you for the root password of the Cloud SQL instance.
* Populate the table by running the script ./populate_table.sh. This script takes two parameters: your bucket name and the root password of your MySQL instance.
* Compute the contingency table for a specific threshold by running the script ./contingency.sh.

Follow the steps in the main text of the chapter to set up a Data Studio dashboard and create charts. Once you are done, delete the Cloud SQL instance since you will not need it for the rest of the book.
