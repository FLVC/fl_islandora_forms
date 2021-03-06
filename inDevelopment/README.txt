FALSCstatewideShortForm.xml
was FALSC11fieldForm.xml

Implementing only the form fields in this standards document (at pages 36 to 85):  https://docs.google.com/document/d/1i9vpvk9Kt4HoW1tr6OfUpy-Jrm_tc4TLKTZm73XthUs/edit  (and locally required fields like IID and flvc:owningInstitution)


FALSC11fieldForm_refinementsNotRemoved.xml

The standard has several places where there is a single item in the Examples, but then many alternatives in the refinement section.  This form still has the refinements included in it.

Here are additional instructions to add to the README for the entire repository after deploying this form:

---(5) FALSCstatewideShortForm.xml---
One of the ?three? forms which is enabled for all content models (other than the Collection Content Model) on Florida Islandora sites. It has a limited number of fields.  This form is not designed to be compatible with the other MODS forms (ie. data entered with Full MODS or MODS Simple entry cannot be editted with this form).

---(6) FALSCstatewideShortForm_NewspaperIssue.xml---
FALSCstatewideShortForm customized for newspaper entry.  This is associated only with the Newspaper Issue Content Model.  The purpose of this separate form is to require a date be entered for each newspaper Issue.  A date is required in order for the issues to display correctly within the larger Newspaper object.
On each new deployment of a MODS form, the FALSCstatewideShortForm_NewspaperIssue form should be recreated by taking a FALSCstatewideShortForm and making the date issued a required field, and making it so that date issued is not collapsed and date created is collapsed by default on going to edit with the form.

---(4) Collection Form FL-Islandora.xml---
Enabled for the Collection Content Model on Florida Islandora sites.  It contains only a few fields (Title, Description, Note, and Language).


accessConditionFormWithRightsstatements_org_AndCreativeCommons_URIasValue_displayLabel.xml

Just the accessCondition fields and the bare minimum of required fields.  This stores the URI for RightsStatements.org or for Creative Commons as the value of the accessCondition element and uses a displayLabel attribute to separate off RightsStatements.org values and Creative Commons values from uncontrolled values.
Changes needed:  The "use and reproduction" and displayLabel fields are shown to users.  Those should be hidden to make the form visually shorter.  Users can't change those values, so no need to see them (or they should see them in an intentional way like a caption or title or something similar).

(Short form with just required fields and accessCondition;  Development is complete on this, but it can be deployed on sites for a clean up project as needed.)




FullMODS_fixingPURLtoNotAPURLflipOnOpen.xml

The Full MODS form has a bug to where when it is used to open a PURL, it will flip the value to "Not a PURL".

MODS Simple Entry and Full MODS handle locDispLabel differently. It looks like this was changed sometime between when Priscilla Caplan shared a version of the Full MODS form on a listserv in March 2014 and when Mike Demers installed the Full MODS form in November 2015.

Since MODS Simple Entry is handling this field correctly, it's good to look at this different and get Full MODS form to where it's handling things more like MODS Simple Entry.





FullMODS_separtingPURLfromOtherLocationInfo.xml

This is something like a perfect fix to the PURL / URL problem in terms of editing MODS.  The problem is that some PURLs on any given site will be in the institution's PURL area and some will be in FCLA's PURL area.  So, this cannot necessarily be used to fix a record where the PURL was flipped - it can't be used if the PURL that is incorrectly as a URL is in FCLA's PURL area.





MODSsimpleEntry_separatingPURL_from_physicalLocation_from_URLs.xml
FullMODS_separatingPURL_from_physicalLocation_from_URLs.xml

Buggy as of Oct. 2018 (opens the same <location> instance in different fields).
Goal is to separate PURL from URL from all location info.  This is because logically a URL for a resource can never be the same location as the physical location.  So those should happen in two separate <location> elements, not within a single <location> element.