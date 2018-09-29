# Cucumber Messages for JavaScript (Protocol Buffers)

[![Build Status](https://travis-ci.org/cucumber/cucumber-messages-javascript.svg?branch=master)](https://travis-ci.org/cucumber/cucumber-messages-javascript)

## HACKING

After building, open the cucumber-messages.d.ts file and run the following
global replace:

    ([\w]+)\?: \(([\w\.\[\]]+)\|null\);
    $1: $2;

This will make the types stricter, not allowing undefined and null values.
This simplifies client APIs, which don't have to include special case logic
for undefined or null properties. It puts the onus on message producers to
always create messages with all the properties set.

For new fields, consumers will have to do undefined/null checks, in case they
are consuming messages from a previous version of the protocol.

We should script this with sed, awk or js.
