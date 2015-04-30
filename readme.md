# WaterDiviner

A watering-hole attack is where an attacker identifies a common resource used by their intended victims and focuses on exploiting that resource to gain a trusted vector.

This tool extracts potential watering holes from text documents, excluding the top 1000 most common domains in order to allow an engineer to focus on more exploitable ones.

_At the moment_, this is all it does.

```
usage: wateringholes.py [-h] [--outfile [OUTFILE]] [--errors [ERRORS]]
                        [--exclude EXCLUDE] [--expand] [--verbose]
                        [--num [NUM]]
                        infiles [infiles ...]

Pull out domains to target for attacks from a body of text.

positional arguments:
  infiles               The input files. Default is STDIN.

optional arguments:
  -h, --help            show this help message and exit
  --outfile [OUTFILE], -o [OUTFILE]
                        Writeable output file. Default is STDOUT.
  --errors [ERRORS], -r [ERRORS]
                        Logfile for warnings. Default is STDERR.
  --exclude EXCLUDE, -x EXCLUDE
                        A domain to exclude from consideration.
  --expand, -p          Include this flag to expand shortened URLs (slow).
  --verbose, -v         Increase verbosity level.
  --num [NUM], -n [NUM]
                        The number of ranks down the watering hole list to
                        report.
```

It can also be imported and used programmatically.

```{python}
import wateringholes
wd = wateringholes.WaterDiviner()
for input in my_input_iterator:
	wd.parse(input)
for domain, count in wd.get_best()
	print(domain)
```
