# motus-metadata-history

This repo tracks changes to the metadata used for tag detections by
the motusServer package.  Each time the cached metadata are updated on
the server, the changes are checked-in to this repo as a new commit,
so that processing done against the updated metadata can record the
commit hash.  This is part of what is needed to let us reconstruct
exactly how data were obtained.

Files:

###tags.csv###
with these columns:
 - motusTagID  integer unique tag ID
 - nomFreq nominal tag frequency, in MHz
 - manufacturer
 - model
 - mfgID
 - period repetition frequency, in seconds

###tag_deployments.csv###
 - motusTagID
 - motusProjectID
 - tsStart unix timestamp of tag deployment start
 - tsEnd unix timestamp of end of deployment
