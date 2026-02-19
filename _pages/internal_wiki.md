---
title: Internal Wiki Procedure Sample
permalink: /internal_wiki/
layout: single
author_profile: true
toc: true
---

**Note**: This is an example of documentation I have created for multiple organizations in the past. All product names, features, and bugs have been changed. I have changed or removed some content to obscure the organization, product, and release contents.

For more information about my process, toolchain, and challenges, see [Procedure: Internal Wiki](./projects.md#procedure-internal-wiki) on the Documentation Projects page.

---

# Adding Metadata Tags to Ditamaps

Our publication tool, ZI, uses metadata tags in the ditamaps to determine how the documents and topics are filtered in the federated search. For example, if a ditamap contains a "ProductOne" metadata tag, ZI displays the published documents containing that tag when a user filters their search to show ProductOne topics.

## The Subject Scheme File

The metadata tags are stored in the SubjectScheme.xml file found in ZI at **Admin > Subject Scheme**.

**Note**: Accessing the Subject Scheme requires Admin access on the ZI portal. The Admin page is available by clicking your name on the portal page. If you do not see the Admin page, then you do not have Admin access. If you cannot access the Subject Scheme, contact a ZI Admin on the Tech Pubs team and they can send you the latest version.

The Subject Scheme file contains three main categories:

- Source: Identifies the document as a Knowledge Article, Documentation, Release Notes, or Known Issue. 
- Products: Identifies the product to which the document belongs.
- Versions: Identifies the specific product version for the document.

**Note**: For Source, the Tech Pubs team uses the `Documentation` and `Release Notes` tags; the Support team uses `Knowledge Article` and `Known Issue`. There is an additional `admin-only` tag that can be used to identify internal documents. Documents tagged `admin-only` display in the Dev Portal only.

## Adding the Metadata Tags to the Ditamap in Heretto

1.  Open the ditamap in Heretto.
2.  Right click the title in the left-side navigation panel, and then click Edit element XML.
3.  Paste the following content on the row under `<title>`:

    ```XML
    <topicmeta>
        <metadata>
            <othermeta content="<<ditamap name_version>>" name="bundle"/>
            <othermeta content="<<version key from SubjectScheme>>" name="facet"/>
            <othermeta content="<<product key from SubjectScheme>>" name="facet"/>
            <othermeta content="docs" name="facet"/>
        </metadata>
    </topicmeta>
    ```

   Tag Descriptions:

    - The 'bundle' tag provides the name of the document bundle (i.e., ditamap) to ZI. Each ditamap should have a unique bundle name. This makes it easier for ZI to differentiate between different versions of the same ditamap. For each ditamap, use the ditamap filename, an underscore, then the version number. For example, if the ditamap filename is "productone_admin.ditamap" and the version is ProductOne 2.1.0, add the following tag:
    `<othermeta content="productone_admin_2.1.0" name="bundle"/>`.

    - The version and product `facet` tags depend on which product and version you are documenting. These tags are found in the Subject Scheme. To request tags for new products and versions, contact the ZI administrator. 

    - The docs `facet` tag is assigned to all customer-facing documents, such as User Guides and Administration Guides, published to the public Doc Portal. If you are adding metadata to a Release Notes ditamap, change the tag to  
    `<othermeta content="rn" name="facet"/>`.

    Here is an example of the complete metadata tag structure added to the ProductOne 2.1.0 Administrator Guide ditamap:

    ```XML
    <topicmeta>
        <metadata>
            <othermeta content="productone_admin_2.1.0" name="bundle"/>
            <othermeta content="ProductOne_2.1.0" name="facet"/>
            <othermeta content="ProductOne" name="facet"/>
            <othermeta content="docs" name="facet"/>
        </metadata>
    </topicmeta>
    ```
    
    These tags are attached to all topics published for this ditamap.
        
4. Click **Save**.

## How Metadata Tags Are Used in the Doc Portal

ZI uses each metadata tag to identify the document to the user in the UI and within the search:

- The `bundle` tag is included in the URL: https://docs.company.com/bundle/productone_admin_2.1.0/

    If you upload different product version of the same document with the same `bundle` tag, then ZI overwrites the published version of the document with the same `bundle` tag. For example, if both ProductOne 2.1.0 and 2.2.0 have the same `bundle` tag, then they overwrite each other when they are published. 
    
    To prevent this, use unique tags for each product version. For example, the recommended bundle tags for two releases could be:
    
    - `<othermeta content="productone_admin_2.1.0" name="bundle"/>` for the 2.1.0 release version. The URL for the published document would be https://docs.company.com/bundle/productone_admin_2.1.0/
    - `<othermeta content="productone_admin_2.2.0" name="bundle"/>` for the 2.2.0 release version. The URL for the published document would be https://docs.company.com/bundle/productone_admin_2.2.0/

    The topics under each document are unique based on the bundle tag. If the same topic exists in multiple releases, ZI treats each instance as distinct and does not overwrite one version's topic when publishing another version. The published topics on the Doc Portal include a **Version** dropdown list where you can select the specific topic version.

- The version and product `facet` tags display on the published topic page.

    Click the tag on the topic page to search for all topics tagged to the product or version, or select the product from the filter on the left (the version filter is unavailable at this time).

- The docs `facet` tag displays on the published topic page as **Documentation**.

    Click this tag to search for all topics tagged **Documentation**, or select **Documentation** from the filter list on the left.
    

