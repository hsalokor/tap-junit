[![Build Status](https://travis-ci.org/dhershman1/tap-junit.svg?branch=master)](https://travis-ci.org/dhershman1/tap-junit)

# tap-junit

Silly small and silly easy XML tap output formatter.

Works with tape and other tap based tests just pipe it into tap-junit and set your output param.

## Changelog

You can checkout the changelog at: https://github.com/dhershman1/tap-junit/blob/master/changelog.md

## Parameters

`-o, --output` - designate where you want the .xml results to output
`-n, --name` - value provided will be the name of the `output.xml` file, otherwise defaults to `tap.xml`

## Installation

~~~ text
npm install -g tap-junit
npm install tap-junit --save-dev
~~~

## Usage

~~~ text
tape test/*.js | tap-junit --output output/test
node test.js | ./node_modules/tap-junit/bin/tap-junit --output output/test
~~~

## Output

```xml
<testsuites>
  <testsuite skipped="false" tests="3" failures="0" errors="0" name="example tests">
    <testcase name="#1 Results should return val"/>
    <testcase name="#2 results should return newVal"/>
    <testcase name="#3 should not change param should return sameVal"/>
  </testsuite>
</testsuites>
```

## Skip Output

**`tap-junit` uses regex currently to determine skipped tests it looks for the `# SKIP` string strictly, so please avoid using this in your test/assert name/msg or you may get incorrect outputs. This is done because none of the current Parsers have solid support for `TODO` or `SKIP` in tap.**

If it is requested I will go back to just having the outputter write blank testsuites and not writing outputs at all when a value is skipped (due to the feedback from tap itself)

Skipped asserts will show up like so:

```xml
<testcase name="#1 test skip extra # SKIP">
  <skipped/>
</testcase>
```

And Fully skiped tests will show up like so:

```xml
<testsuite skipped="true" tests="0" failures="0" errors="0" name="SKIP skipped test"/>
```
