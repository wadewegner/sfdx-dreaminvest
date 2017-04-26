# sfdx-dreaminvest

This is an SFDX-ified version of Christophe Coenraets **Mutual Fund Explorer** Lightning App. You can find details on his on the post [Mutual Fund Explorer: A New Lightning Components Sample Application](https://developer.salesforce.com/blogs/developer-relations/2017/04/mutual-fund-explorer-new-lightning-components-sample-application.html).

I converted this app to SFDX by doing the following:

1. Installed the unmanaged package into an org (I used a scratch org but it doesn't matter).

2. Created a new SFDX workspace: `sfdx force:workspace:create -n sfdx-dreaminvest`

3. Created a new directory: `mkdir mdapipackage`

4. Invoked a metadata retrieve on the package: `sfdx force:mdapi:retrieve -s -r ./mdapipackage -p DreamInvest`

5. Retrieved the package: `sfdx force:mdapi:retrieve --jobid [JOBID] --retrievetargetdir ./mdapipackage`

6. Unzipped the paackage: `unzip mdapipackage/unpackaged.zip -d mdapipackage/`

7. Removed the zip: `rm mdapipackage/unpackaged.zip`

8. Converted the source: `sfdx force:mdapi:convert -r mdapipackage/`

9. Removed the old source: `rm -rf mdapipackage`

Now I can push and run:

1. Create a scratch org: `sfdx force:org:create -s -f config/workspace-scratch-def.json`

2. Push the source into my org: `sfdx force:source:push`

3. Assign the user to the permset: `sfdx force:user:permset:assign -n DreamInvest`

4. Open the org and run app: `sfdx force:org:open`