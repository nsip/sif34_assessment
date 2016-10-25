# sif34_assessment
Assessment Objects to be added to SIF-AU 3.4 (excluding NAPLAN objects)

The NSIP Data Standards Working Group met on Friday 2016-10-21, to discuss the requirements for assessment data objects in 
Australian Education. The objects convering NAPLAN assessment were kept out of scope. [NAPLAN Results Reporting](https://github.com/nsip/naplan-results-reporting), 
[NAPLAN Registration](https://github.com/nsip/registration-data-set)

##Starting point

At the start of the workshop, there were two objects in SIF 3.4 addressing formative assessment: GradingAssignment and GradingAssignmentScore. There was also a proposal worked out in conjunction with CEO Melbourne, for StudentGrade, capturing the teacher judgement of a student's progress in a subject, against specific curriculum objectives: 

![Assessment #1](https://github.com/nsip/sif34_assessment/blob/master/assessment%20update1.png)

These objects were the departutre point for the workshop.

##Key findings from Workshop: General

* NAPLAN SIF objects will remain idiosyncratic
* It should be possible to use the same set of objects for formative and summative assessment, at a first cut
* Objects specific to particular assessment activities or use cases may be added as needed

##Key conclusions from Workshop: Immediate changes

The following conclusions are referred against this entity-relationship diagram.

![Assessment #2](https://github.com/nsip/sif34_assessment/blob/master/assessment%20update2.png)

###Assessment Instrument

* School authorities are rarely interested in gathering the test instrument (assessment form, assignment); they are more interested in the assessment results.
* However the test instrument may be consulted to make sense of the results.
* The test instrument should at least be described at a sufficient level of detail, for the test to be understood.

OUTCOME:
* At this stage, the assessment instrument is represented as the link from GradingAssessment to an online resource or binary attached resource
* The instrument is accompanied by a descriptor.
* At a later stage, particulary in summative assessment, an AssessmentItem object may be provided. This is already the case in NAPLAN.

###Assessment Purpose

* The purpose of assessment differentiates different kinds of assessment, as context
* That includes where the assessment is intended for
* The event stream is different for different modes of assessment; e.g. evidence of attainment
* Purposes of assessment include:
  * Teachers scoring student work
  * Teachers reporting on students’ progress vertically
  * Teachers reporting on students’ progress to parents
  * Diagnostic formative
  * Paedagogical formative (which often ends up being diagnostic at a different time scale)


OUTCOME
* An Assessment Purpose field is added to GradingAssignment
* The assessment purpose will likely need to be enriched significantly, to provide proper context to assessment objects

###Syllabus
* Assessment needs to be contextualised against the syllabus or curriculum being taught, for the data exchange to be interpretable.
* The syllabus is heterogeneous, and the existence of the Australian Curriculum does not render other syllabuses obsolete.
* The syllabus can include local ad hoc entries, and entries specific to a student (learning plan).
* Cannot always mandate a syllabus link
* An assessment may need to align to multiple curricula (e.g. International Baccalaureate)
* School authorities use syllabus links to determine how much of the curriculum has been covered through assessment

OUTCOME:
* Both GradingAssignment and StudentGrade link to zero or more learning standards
* The learning standards are encoded as an option of: LearningStandardItem RefID; Australian Curriculum URL; or Curriculum/Statement pair. This reflects the following requirements:
  * The learning standard object is not presupposed to be in the Australian Curriculum, or mapped to the Australian Curriculum
  * The learning standard object does not require the client to reconstruct the hierarchy it is situated in (though that option is available)
  * The learning standard object is not presupposed to be formally defined in a hierarchy
  * The learning standard object is not presupposed to belong to a formal curriculum. It may belong to an individual learning plan, or an ad hoc learning objective
  * Not all learning standard objects are presupposed to belong to the same curriculum

###Expected Score
* The score received for an assessment is often contrasted against the expected or predicted score
* The expected score can be used to substitute for the received score, where the received score is unavailable (the student has not done the assessment, and will not be penalised for it)

OUTCOME:
* GradingAssignment has two links to GradingAssignmentScore. 
  * The current mandatory link remains, but becomes optional, and indicates the received score. 
  * An additional optional link is added, to indicate the expected or predicted score.

###Compositionality
* Assessments can be aggregated into other assessments
* Assessments can be grouped by semester; by practical or written statues, and by other  categories
* The report of a student’s progress over a marking term is based on assessments that they have undergone during the term


OUTCOME
* A GradingAssignment can consist of other GradingAssignments, recursively
* The Category rubric of GradingAssignment remains open-ended, and can be used to describe a grouping of assessments.
* The StudentGrade object may link to the GradingAssignmentScore objects that it aggregates over


##Shared Knowledge
![Assessment #3](https://github.com/nsip/sif34_assessment/blob/master/assessment%20update2.png)

###Setup
* There needs to be agreed definitions between sender and receiver of several contextual entities around assessment, if the data exchange around assessment is to make any sense.
* That agreement can occur out of band (mutual knowledge,  but the sender and receiver need to have the option of making the agreement explicit, as part of an initial handshake around the data exchange).
* The agreed knowledge between sender and receiver can change for any two parties, and even for any given exchange.
OUTCOME:
* Optional contextual objects will be linked to assessment, to provide information necessary to interpret them
* Pre-Exchange handshaking will determine whether these contextual objects will need to be exchnaged. 
* Within an enterprise, these contextual objects typically will not be exchanged, as their value will be understood.

###Score
* The agreed knowledge includes the interpretation of marks (minimum value, maximum value, distribution, metric)
* The move from local grading to standardised grading may occur only on import of assessment data.
* Standardising across multiple grading schemes is difficult; vendors can end up supporting dozens of different file formats
* Often the original grade is displayed as is, and not processed
OUTCOME:
* An optional MarkValueInfo object is linked to all instances of scores and marks, to provide the interpretation of those marks
* That object is not required if the marks are not to be interpreted further
* That object is not required if the marks are normalised to a mutually agreed scale before data exchange


###Syllabus source
* The agreed knowledge includes the source of the syllabus or curriculum assessed against.
* There may be a need for an external register of learning standards (further discussion)
OUTCOME
* A Syllabus source object or tag will be added optionally to curriculum statements


##Scoring iterations
![Assessment #4](https://github.com/nsip/sif34_assessment/blob/master/assessment%20update4.png)

* The scoring process may need to be captured
* Successive submissions of drafts can be tracked
* The student artefact (script) may be retained
* Successive attempts at an assessment may be scored differently

OUTCOME
* A Grading Assignment Submission Draft object will be added
* The object may include the student artefact
* The object is timestamped
* The object will indicate which iteration of submission the draft reflects
* Each Grading Assignment Submission Draft may be scored separately. This is reflected in an optional link to a separate instance of GradingAssignmentScore

##Other conclusions from Workshop:


* Test rubrics will need to be captured (deferred)

