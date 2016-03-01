https://github.com/KantaraInitiative/wg-uma/wiki/UMA-Legal:-Mapping-Between-UMA-and-Agency-Law
UMA Legal: Mapping Between UMA and Agency Law
_______________


Because Agency law is well understood and relatively consistent in various jurisdictions around the world, and because it is more fundamental than contract law, it is valuable to map UMA parties and flows to interpretations of Principal, Agent, and Third Party roles. This is a first step towards structuring an UMA-related transaction.

# Understanding and Applying the Law of Agency

The [Restatement (Third) of the Law of Agency](https://users.wfu.edu/palmitar/ICBCorporations-Companion/Conexus/UniformActs/Restatement(third)Agency.pdf) is the best available source of agency law rules and should be used to inform our analysis.

To complete this exercise well, it is important to actually understand and be able to apply Agency Law correctly to relevant scenarios and use cases.  Legal "Fact Patterns" and "Hypothetical Cases" are common tools in the law for achieving this type of proficiency.  Please take a look at the [agency law resources](https://github.com/KantaraInitiative/wg-uma/wiki/UMA-Legal:-Mapping-Between-UMA-and-Agency-Law#solving-agency-law-fact-patterns-and-hypothetical-situations) below, to develop a basic working understanding and ability to apply these rules. These materials were selected specifically for use by the UMA Legal Subgroup and reflect the method used by law.MIT.edu to prep non-lawyers for team participation in multi-disciplanary, cross-functional business, legal and technical professional development and training.  

## Mapping OAuth 2 to Agency Law

Generally, the party we are most concerned with is "Alice", our personification of an individual serving as an UMA resource owner. Thus, she is typically the Principal. See the [Terminology](https://github.com/KantaraInitiative/wg-uma/wiki/UMA-Legal:-Terminology) page in order to understand terms used on this page.

UMA is built on the OAuth 2 protocol, so OAuth 2 is fundamental to UMA.

A layman's description of OAuth entities can be found in the HEART use cases; for example, [Elderly Mom with Family Caregiver](https://docs.google.com/document/d/1V3e_fDH63fNDsV-WOGKcyg0ebuW165DOpjY_RcuMk4U/edit#heading=h.h6oukcn7dpmy). Though the use case is health-related, the OAuth description is not.

### Basic OAuth 2 Flow

Here is a very brief list of typical OAuth technical interactions that helped us analyze the Agency proposition (leaving out many complex security-related details that are unrelated to our purposes here). Note that in OAuth, it can be assumed that the AS and RS software are co-located and are run by the same party. Hence, we say "AS/RS".

1. AS gives client credentials to C
1. (in any order with the above) AS/RS gives user credentials to RO
1. RO logs in to C
1. RO chooses AS/RS from C
1. C redirects RO to AS
1. RO logs in and consents to access token issuance
1. AS issues access token for C to use
1. AS redirects RO back to C
1. C eventually gets RO back and also gets access token
1. (ongoing) C uses access token at RS on behalf of RO, possibly operated live by RO or possibly with RO offline
1. (later) AS might expire the access token, requiring C to use a refresh token (uninteresting for our purposes here) or requiring the RO to engage in access token issuance consent again
1. (later) RO might revoke the access token

### Proposal for Mapping OAuth to Agency Law

We choose to make the (human) Authorizing Party the Principal. The AS/RS Operator is therefore the Third Party, and the Client Operator is the Agent. This is true even when the triangle among them hasn’t been fully formed yet.

Questions:

* Is it possible to see the AS/RS Operator as the Authorizing Party's Agent and the Client Operator as the Third Party instead, depending on the kind of application functionality and which side (service or app) the individual feels more aligned with? If so, what difference does the switch make?

* How do we deal with parties that act as Agents for multiple other parties, a la “brokers”?

* AS and RS are almost certainly run by the same operator; trust between is established in some unknown fashion
Thus, two legs of the triangle are formed. Later,the third leg of the triangle will be formed, enabling a full application of the roles we have chosen. Do we care about the “private” agreements that might have been formed for each of these two legs?

## Mapping UMA to Agency Law

By contrast with OAuth, UMA enables an individual resource owner to have more control over 

A layman's description of UMA entities can be found in the HEART use cases; for example, [Elderly Mom with Family Caregiver](https://docs.google.com/document/d/1V3e_fDH63fNDsV-WOGKcyg0ebuW165DOpjY_RcuMk4U/edit#heading=h.ky8slquqkq9w). Though the use case is health-related, the UMA description is not.

### Proposal for Mapping UMA to Agency Law

Adrian, with Eve's input, developed the following analysis of UMA in light of Agency law, with embedded interpretation and questions. *This needs careful review and is not normative output of the subgroup.*

1. The unique and essential value of UMA is the ability for a Principal to specify a standards-based Agent to a Third Party.
  1. The UMA resource owner (RO) is the Principal, the UMA authorization server (AS) is the Agent, and the UMA resource server (RS) is the Third Party.
1. The Third Party derives value from a “safe harbor” protection when sharing data that is under its control.
  1. The UMA RS derives value from the relationship established with the AS when the RS is releasing the data under the RS’s control.
1. The Principal derives value from the ability to delegate control to the same accountable proxy across a wide range of third parties.
  1. The UMA RO gets benefit from leveraging a single UMA AS over a wide range of (or at least multiple) RS’s. The UMA AS may also get a benefit if this is its business model (authorization-as-a-service).
1. The Principal has a direct relationship with the Third Party and can use that to introduce the Agent as well as to notify the Third Party of changes to the Agent relationship.
  1. The UMA RO has a direct relationship with the UMA RS already, independent of the AS, and the RO can introduce the RS to the RO’s AS.
1. The Principal grants Actual Authority (3.01) to the Agent to express assent for the Agent to act on the Principal’s behalf.
  1. The UMA RO, by virtue of authorizing the issuance of the UMA protection API token (PAT), signals its approval for the Third Party to use the Agent for resource protection (spec). The UMA RS retains the ability to protect any subset of the RO’s resources that it likes using different means or different Agents (spec).
1. The contract between the Principal and the Third Party that introduces the Agent is the "ROI Form" (*needs to be defined and taken out of a healthcare context*) and establishes Apparent Authority (2.03) and (3.03). The ROI Form includes provision for Notification (5.01) to and by the Agent.
  1. This contract presumes a “new ROI form” that is digital. Could it encompass the PAT issuance process, for one? The PAT process could display terms and conditions on top of just the token issuance.
1. Apparent Authority ends when the Third Party that an Agent deals with is reasonably notified. (3.11)
  1. The process in #6 should cover this.
1. The Agent may be anyone or anything, including open source software built by the Principal. (3.05)
  1. How much real choice does the RO get over their choice of AS? Is it possible for a Third Party to refuse to work with a Principal’s Agent? If so, on what grounds?
1. The UMA Requesting Party can be a coprincipal (3.16) in the Agent but this would require an Actual Authority relationship between with the Agent which might compromise the Requesting Party’s privacy.
  1. The UMA requesting party (RqP) develops a similar/reciprocal, though somewhat weaker relationship with the UMA AS than does the UMA RO. E.g., the UMA RqP, by virtue of authorizing the issuance of the UMA authorization API token (AAT), signals its approval for the [UMA client -- what is it legally?] to use the Agent for seeking and gaining authorization to the RO’s recources.
1. ??? What are the UMA Client and the Requesting Party under Agency Law?
  1. Dunno.
1. The Third Party (UMA-RS) that registers an Agent (UMA-AS) deserves a Payment (8.14) to offset their cost in offering the API and their opportunity cost of foregoing the branding and advertising benefits of a manual Web portal that would otherwise tax the Principal's attention.
1. The Third Party is encouraged to provide a choice of Agents for Principals that don't already have one. The Agent can be changed by the Principal at any later time. This is not required by Agency Law but it would provide a large incentive for RSs to adopt UMA before someone else does.
1. ??? Can an identity provider or credential broker be a subagent (3.15) of the Agent as a means to protect the Requesting Party’s privacy?
  1. Dunno.
1. Based on agency law and the analysis above, here is a list of the “minimum viable product” requirements for a technical protocol involving a Principal, an Agent, and a Third Party. The endpoints or parameters would be:
  1. a human-readable (PDF/HTML) version of the applicable contract (ROI Form?),
  1. agent URI or human-readable means to introduce the agent,
  1. agent choices offered by third-party for principals that don’t have one,
  1. protected resource URI and human-readable name for display by the Agent,
  1. endpoints for notification of contract changes or cancellation (in both directions), including public keys to enable secure and accountable communications,
  1. endpoint to notify agent of contract activity including a description, link, or reference to the client and requesting party involved,
  1. generic contract terms including expiration date of contract, option for unilateral cancellation, read, write, or read/write transactions on the resource,
  1. an account where the RS can receive payment and a means to link payment to an authorized transaction,
  1. names and signatures of both the resource owner and the third-party.


# Solving Agency Law Fact Patterns and Hypothetical Situations

A FRAMEWORK OF ANALYSIS FOR THE LAW OF AGENCY
http://scholarship.law.umt.edu/cgi/viewcontent.cgi?article=1408&context=mlr

Simple Primer on Legal Reasoning and Analysis:
* http://www.lawnerds.com/guide/irac.html

**Bar Exam written Agency Law Fact Patterns and Example "Good Answers"**

State of CA Bar Exam:  See Question 6: 
* http://admissions.calbar.ca.gov/portals/4/documents/gbx/February-2013-CBX%20Selected%20Answers%20Essays.pdf

State of MD Bar Exam: See Question #2 and Representative Good Answer #1:
* http://mdcourts.gov/ble/examanswers/2012/201207gbrepresentativegoodanswers.pdf

State of GA Bar Exam:
* Questions: https://www.gabaradmissions.org/feb02q
* Good Answers: https://www.gabaradmissions.org/feb02a

Example "Killer Outline" of Star Law Students from Yesteryears
**I notices this outlines has a lot of hypothetical scenarios and solutions and are worth a look.  Such killer outlines are the source of much knowledge among law students and are passed down to future entering classes with care and deep appreciation** 

* http://www.stcl.edu/students/SBA%20Outline%20Bank/A_PProblems%5B1%5DTilton.doc
* https://www.hitpages.com/doc/6428878310473728/29/


# Understanding Agency Law Overall

ILLINOIS PATTERN JURY INSTRUCTIONS-CIVIL AGENCY LAW 
Agency law instructions for juries for use in tort cases in which there is an
issue of vicarious liability based on principles of agency. 
* http://www.illinoiscourts.gov/circuitcourt/civiljuryinstructions/50.00.pdf

* Creative Commons Compilation on The Legal Environment and Business Law:  * http://2012books.lardbucket.org/books/the-legal-environment-and-business-law-executive-mba-edition/index.html
 Agency Law Chapters:
* http://2012books.lardbucket.org/books/the-legal-environment-and-business-law-executive-mba-edition/s14-relationships-between-principa.html
* http://2012books.lardbucket.org/books/the-legal-environment-and-business-law-executive-mba-edition/s15-liability-of-principal-and-age.html

Digital Commons Network: Agency Commons
* http://network.bepress.com/law/agency/

See: "Defining Agency And Its Scope"
* http://scholarship.law.duke.edu/faculty_scholarship/3417/

Also see: Simple study-aid summary of basic principles:
 * Under Il law: https://quizlet.com/12759249/il-bar-exam-agency-and-partnership-flash-cards/
 * Under MD law: https://quizlet.com/17361865/agency-partnership-bar-exam-md-flash-cards/

 ##  Understanding Key Specific Aspects of Agency Law

The Mechanisms of Control
 * http://scholarship.law.duke.edu/faculty_scholarship/864/

 The Contours and Composition of Agency Doctrine: Perspectives from History and Theory on Inherent Agency Power
 * http://scholarship.law.duke.edu/cgi/viewcontent.cgi?article=6042&context=faculty_scholarship

 Agency Models in Law and Economics (by Posner)
   * http://www.law.uchicago.edu/files/files/92.EAP_.Agency.pdf

 SQUARING UNDISCLOSED AGENCY LAW WITH CONTRACT THEORY
 * http://www.bu.edu/rbarnett/squaring.htm

 Liability to Third Parties and Termination
 * http://abogado.pbworks.com/w/file/fetch/43886739/chp32.pdf

## Electronic Agents and Automated Transactions

See: The conclusion of contracts by software agents in the eyes of the law.
* http://www.researchgate.net/publication/221456172_The_conclusion_of_contracts_by_software_agents_in_the_eyes_of_the_law

ALSO See: ARTIFICIAL AGENTS AND THE CONTRACTING PROBLEM: A SOLUTION VIA AN AGENCY ANALYSIS
* http://illinoisjltp.com/journal/wp-content/uploads/2013/10/Chopra.pdf

The Use of Electronic Agents Questioned Under Contractual Law: Suggested Solutions on a European American Level
* http://repository.jmls.edu/cgi/viewcontent.cgi?article=1184&context=jitpl

Also See: Reconciling the Promise of Agency Law Doctrine with Contract, Tort and Property Law Restrictions on Electronic Agent Deployment
* https://faculty.ist.psu.edu/bagby/Pubs/Bagby-eAgency-Hurst2-041.pdf

Legal Issues in Agents for Electronic Contracting
* http://www.computer.org/csdl/proceedings/hicss/2005/2268/05/22680134a.pdf

Agency Law in Cyberspace
* http://scholarship.law.duke.edu/faculty_scholarshttps://www.hitpages.com/doc/6428878310473728/29/hip/1322/

Also See:  Computer Programs Are People, Too: How treating smart programs as legal persons could change privacy as we know it.
* http://www.thenation.com/article/computer-programs-are-people-too

Also See: Automating Conflict-Of-Interest Reporting The FTC’s new rules mandating blogger conflict-of-interest disclosure are based on antiquated technological assumptions.
* https://www.ftc.gov/sites/default/files/documents/public_events/how-will-journalism-survive-internet-age/snider1.pdf
