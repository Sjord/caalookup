## caalookup

Look up CAA records as specified by RFC8659.

## CAA records

Certification Authority Authorization, or CAA, are DNS records that indicate which Certificate Authority (CA) can issue certificates for a particular domain. A CAA record that indicates that Let's Encrypt may provide certificates may look as follows:

    0 issue "letsencrypt.org"

## Resolving algorithm

`caalookup` checks the given domain and each parent domain for CAA records. If it finds a CNAME it will follow that, but not check all the parents of the target CNAME. This behaviour differs from RFC6844, which is obsolete.

## Usage

Install with the usual go commands:

    $ git clone https://github.com/Sjord/caalookup/
    $ cd caalookup
    $ go get
    $ go build

And run with a fully qualified domain name:

    $ ./caalookup deny.permit.basic.caatestsuite.com.
    deny.permit.basic.caatestsuite.com.	59	IN	CAA	0 issue "caatestsuite.com"
