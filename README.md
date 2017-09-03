# motus-metadata-history

This repo tracks changes to the metadata used for tag detections by
the motus server.  Each time the cached metadata are updated on the
data-processing server, the changes are checked-in to this repo as a
new commit.  Every time a batch of data is processed, the current
commit hashes for these metadata are recorded in the `batchParams`
table.  This is part of what is needed to let us reconstruct exactly
how data were processed and why.

Files:

### tags.csv ###
with these columns:
 - motusTagID  integer unique tag ID
 - manufacturer
 - model
 - codeset
 - nomFreq nominal tag frequency, in MHz
 - mfgID
 - period repetition frequency, in seconds

### tag_deployments.csv ###
 - motusTagID
 - motusProjectID
 - tsStart unix timestamp of tag deployment start
 - tsEnd unix timestamp of end of deployment
 - tsStartCode method for calculating start date
 - tsEndCode method for calculating end date

### parameter_overrides.csv ###
 - motusProjectID INTEGER
 - serno CHAR(32),                            -- serial number of device involved in this event (if any)
 - tsStart FLOAT(53),                         -- starting timestamp for this override (Lotek only)
 - tsEnd FLOAT(53),                           -- ending timestamp for this override (Lotek only)
 - monoBNhigh INT,                            -- ending boot session for this override (SG only)
 - monoBNlow INT,                             -- starting boot session for this override (SG only)
 - progName VARCHAR(16) NOT NULL,             -- identifier of program; e.g. 'find_tags'
 - paramName VARCHAR(16) NOT NULL,            -- name of parameter (e.g. 'minFreq')
 - paramVal FLOAT(53) NOT NULL,               -- value of parameter
 - why TEXT                                   -- human-readable reason for this override
