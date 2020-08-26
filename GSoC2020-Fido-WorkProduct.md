# GSoC 2020 Work Product | OpenAstronomy | Fido

## Project Metadata

- **Title**: Metadata searches using Fido
- **Student**: [Abhijeet Manhas](https://github.com/abhijeetmanhas)
- **Mentors**: [Stuart Mumford](https://github.com/Cadair), [Nabil Freij](https://github.com/nabobalis)
- **Organisation**: [Open Astronomy](https://openastronomy.org/)
- **Sub-Org**: [SunPy](https://sunpy.org)
- **Repository**: [sunpy](https://github.com/sunpy/sunpy/)
- **Edition/Year**: 2020

## Description

SunPy's `Fido` stands for Federated Internet Data Obtainer.
It is a versatile and flexible search interface that allows users to query data for various search attributes and different clients.
It is used for fetching solar physics data from various HTTP and FTP archives, and now from web-services too.

The first part of the project was to extend the ability for `dataretriever` clients to specify what metadata about the results should be displayed in their `QueryResponse` objects. This was achieved by refactoring in the `net` submodule and additions to the scraper.
Sunpy's `scraper` is now able to extract metadata from filenames using their URLs.
An external module, `parse` was added to SunPy to ease the retrieval of `attrs`.
`GenericClient` was redesigned and now `show()` method can be used to specify the columns to be displayed in search responses.
The QueryResponses now can even show `SatelliteNumber`, `Wavelength`, `Level`, `Provider`, `Physobs`, etc. in their tables which wasn't possible earlier.

The second part was more closer to the central theme of the project. A base Class, `BaseQueryResponseTable` was created for clients that return mostly tabular data.
`JSOCResponse`, `HEKResponse`, and `HECResponse` now inherit this class and it reduced code duplication.
After registering the search "attrs" supported by these metadata clients, they were made compatible with Fido. There were a couple of other issues resolved alongside the big pull request for these changes.

In the last part, I wrote the developer guide for Fido. I added examples of how to use the new functionality. `UnifiedResponse` know supports string-based indexing.
It makes retrieving individual provider responses from a Fido result easy, as opposed to int based indexing. Many reviews on old PRs were resolved in the last phase.

## Progress

I have been blogging my progress on this project biweekly on Medium. I highly recommend going through [my GSoC blogposts](https://medium.com/@abhimanhas). They contain Github gists, ipython notebooks, and code snippets that will make you understand the project better.

1. [The Start of my summer with SunPy](https://medium.com/@abhimanhas/gsoc-2020-the-start-of-my-summer-with-sunpy-d8af558ad399).
2. [The Coding period commences!](https://medium.com/@abhimanhas/gsoc-2020-the-coding-period-commences-b2eee33f274e).
3. [Generalization of Clients](https://medium.com/@abhimanhas/gsoc-2020-generalization-of-clients-1879f5dfe436).
4. [End of the First Half](https://medium.com/@abhimanhas/gsoc-2020-end-of-the-first-half-ec4589cc452f).
5. [Metadata searches using Fido](https://medium.com/@abhimanhas/gsoc-2020-metadata-searches-using-fido-909bda98b771).
6. [Polishing my code](https://medium.com/@abhimanhas/gsoc-2020-improvising-the-code-c2d1683fe428).
7. [Thus Ending](https://medium.com/@abhimanhas/gsoc-2020-thus-ending-acd30ed987ae).

## Links to Work Done

### Pull Requests made
1. Reduced time for Goes Suvi tests https://github.com/sunpy/sunpy/pull/4131
2. Fixed href in scraper https://github.com/sunpy/sunpy/pull/4132
3. Fixed wrong sat no. in XRS overlapping URLs https://github.com/sunpy/sunpy/pull/4288
4. Added a show method for base client https://github.com/sunpy/sunpy/pull/4309
5. Method to extract metadata from URL in scraper https://github.com/sunpy/sunpy/pull/4313
6. Post Search filters again for VSO https://github.com/sunpy/sunpy/pull/4011
7. Gong Synoptic Fido client https://github.com/sunpy/sunpy/pull/4055
8. VSO fetch fix https://github.com/sunpy/sunpy/pull/4026
9. Redesign GenericClient https://github.com/sunpy/sunpy/pull/4321
10. Metadata clients compatible with Fido https://github.com/sunpy/sunpy/pull/4358
11. Fido dev-guide https://github.com/sunpy/sunpy/pull/4387
12. Method to know time ranges in scraper https://github.com/sunpy/sunpy/pull/4419

### Issues I worked upon
1. Inconsistent Ordering in VSO Results https://github.com/sunpy/sunpy/issues/3922
2. VSO fails to filter response https://github.com/sunpy/sunpy/issues/3833
3. Slow fetch in the test for SUVI Client https://github.com/sunpy/sunpy/issues/4099
4. Wrong Satellite number in overlapping URLs https://github.com/sunpy/sunpy/issues/4207
5. QueryResponses can't show desired columns https://github.com/sunpy/sunpy/issues/556
6. Broken VSO fetch for some providers https://github.com/sunpy/sunpy/issues/3734
7. Support for Gong Synoptic Maps client https://github.com/dstansby/pfsspy/issues/165
8. GenericClient not knowing file time ranges https://github.com/sunpy/sunpy/issues/3715
9. GOES hard-codes dates for available satellites https://github.com/sunpy/sunpy/issues/3337
10. DR Clients can't specify columns to be shown https://github.com/sunpy/sunpy/issues/3321
11. Generalize can_handle_query https://github.com/sunpy/sunpy/issues/3306
12. Inconsistent wavelength tuple https://github.com/sunpy/sunpy/issues/2314
13. Integrate metadata clients in Fido https://github.com/sunpy/sunpy/issues/2744
14. Wrong links in WSDL helio parser https://github.com/sunpy/sunpy/issues/2032
15. JSOC ignores keys attrs https://github.com/sunpy/sunpy/issues/3293
16. JSOC search_metadata returns pandas data frame https://github.com/sunpy/sunpy/issues/3941
17. JSOC returns empty IRIS blocks https://github.com/sunpy/sunpy/issues/2002

### Reported Issues
1. Wrong XRS sat_no in overlaps https://github.com/sunpy/sunpy/issues/4207
2. Skip HELIO tests for not-reachable server https://github.com/sunpy/sunpy/issues/4243
3. Failing fermi remote doctest https://github.com/sunpy/sunpy/issues/4211
4. Wrong GOES HEK time-series plot https://github.com/sunpy/sunpy/issues/4429
5. Client unaware of time ranges https://github.com/sunpy/sunpy/issues/3715
6. Scraper refactoring https://github.com/sunpy/sunpy/issues/4336
