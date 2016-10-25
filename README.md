# sif34_assessment
Assessment Objects to be added to SIF-AU 3.4 (excluding NAPLAN objects)

The NSIP Data Standards Working Group met on Friday 2016-10-21, to discuss the requirements for assessment data objects in 
Australian Education. The objects convering NAPLAN assessment were kept out of scope. [NAPLAN Results Reporting](https://github.com/nsip/naplan-results-reporting), 
[NAPLAN Registration](https://github.com/nsip/registration-data-set)

Key conclusions from Workshop:

* Assessment needs to be contextualised against the syllabus or curriculum being taught, for the data exchange to be interpretable.
* The syllabus is heterogeneous, and the existence of the Australian Curriculum does not render other syllabuses obsolete.
* The syllabus can include local ad hoc entries, and entries specific to a student (learning plan).
* Cannot always mandate a syllabus link
* An assessment may need to align to multiple curricula (e.g. International Baccalaureate)
* School authorities use syllabus links to determine how much of the curriculum has been covered through assessment
OUTCOME:


* There needs to be agreed definitions between sender and receiver of several contextual entities around assessment, if the data exchange around assessment is to make any sense.
* That agreement can occur out of band (mutual knowledge,  but the sender and receiver need to have the option of making the agreement explicit, as part of an initial handshake around the data exchange).
* The agreed knowledge between sender and receiver can change for any two parties, and even for any given exchange.
* The agreed knowledge includes, at a minimum, the interpretation of marks (minimum value, maximum value, distribution, metric); and the source of the syllabus or curriculum assessed against.
OUTCOME:

* The move from local grading to standardised grading may occur only on import of assessment data.
* Standardising across multiple grading schemes is difficult; vendors can end up supporting dozens of different file formats
* Often the original grade is displayed as is, and not processed


* School authorities are rarely interested in gathering the test instrument (assessment form, assignment); they are more interested in the assessment results.
* However the test instrument may be consulted to make sense of the results.
* The test instrument should at least be described at a sufficient level of detail, for the test to be understood.

* Assessments can be aggregated into other assessments
* Assessments can be grouped by semester; by practical or written statues, and by other  categories

* The report of a student’s progress over a marking term is based on assessments that they have undergone during the term


* There may be a need for an external register of learning standards


* NAPLAN SIF objects will remain idiosyncratic
* It should be possible to use the same set of objects for formative and summative assessment, at a first cut


* Test rubrics need to be captured




Other conclusions from Workshop:

* The scoring process may need to be captured
* Successive submissions of drafts can be tracked
* The student artefact (script) may be retained
* Successive attempts at an assessment may be scored differently

* The purpose of assessment differentiates different kinds of assessment, as context
* That includes where the assessment is intended for
* The event stream is different for different modes of assessment; e.g. evidence of attainment

* The score received for an assessment is often contrasted against the expected or predicted score
* The expected score can be used to substitute for the received score, where the received score is unavailable (the student has not done the assessment, and will not be penalised for it)


* Purposes of assessment include:
* Teachers scoring student work
* Teachers reporting on students’ progress vertically
* Teachers reporting on students’ progress to parents
* Diagnostic formative
* Paedagogical formative (which often ends up being diagnostic at a different time scale)

