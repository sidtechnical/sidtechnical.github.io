---
layout: post
title:  'IEEE S&P (Oakland) Student PC experience'
categories: 
  - blog
tags:
  - reflections
published: true
---

I was one of the [student PC members][studentpc] for the **39th IEEE Symposium on Security and Privacy** (IEEE S&P Oakland). Since this was my first review experience for a reputed academic conference, I thought of writing down my experience for my own (as well as others) future reference.

"Student PC" or shadow PC mainly consists of doctoral students and post-docs to mimick the actual review procedures of a typical academic conference by shadowing the actual program commitee (comprising of professors and other industry professionals). It is becoming an official part of good conferenes, for example, earlier with [Privacy Enhancing Technologies Symposium (PETS)][PETS] and [The Network and Distributed System Security Symposium (NDSS)][ndss], and starting from last year, also with IEEE S&P Oakland. It is mainly for the early-stage research students to gain first-hand experince of being part of a review committee.

This year's student PC was headed by [**Prof. Thorsten Holz**][thorsten], Ruhr-University Bochum, who did a great job of introducing all of the student PC members to the review process and guided all of us throughout different stages of the process.

The whole review process was divided into following parts:
1. Pre-review tele-meeting.
2. Bidding of the papers, followed by paper assignment to the student PC for reviewing.
3. Actual review of the papers assigned, followed by online discussion.
4. In-person meeting with all the other student PC members in the Google office, New York.

## 1. Pre-review tele-meeting

This tele-meeting included a nice overview of future steps that the student PC members are expected to do. Prof. Thorsten gave a brief overview ([his presentation slides][instructions]) of all the things that we should be aware of. First and foremost step was to register ourselves as a reviewer to the submission system (i.e. **HOTCRP**). While most of were familiar with such submission systems (of course, as authors), this was the first time we all got a chance to sneak behind the scenes of review process. We were given instructions on our goals, How program committees operate, considerations of PC members, conflicts disclosure, What makes a good review, and the timeline of next steps. 

<i class="fa fa-book" aria-hidden="true"></i> *Writing a good review*: [Thoughts on Reviewing][r1], [Notes on Constructive and Positive Reviewing][r2] and [How NOT to review a paper: The tools and techniques of the adversarial reviewer][r3].


## 2. Paper bidding and assignment

We were then asked to bid **for or against** the papers that each of us wanted to review. Depending on the review/submmission system, positive bid score means the reviewer is interested to review the paper and the negative score to show that reviewer is not interested. Typically, these scores range from -20 to +20. The **conflicts** (e.g. reviewer is a co-author, previous co-worker/collaborator in the past two years, primary advisor no-matter how long ago, etc.) are marked with **-100**.

If the reviewers bid, their chances that they are asssigned to review the paper of their choice is high. Lazy reviewers who fail to bid for or against will get random papers (papers that are disposed by other reviwers) that will be assigned by the PC chair. Most of us got the papers that we wanted to review. Of course, we chose those papers where we felt we are comfortable with!

## 3. Reviews and discusson

The review included us to fill in the following fields. All of us were assigned about 8 to 10 papers, and we had to fill in these details for each of those papers. Each paper had 3-4 reviewers and everyone has to individually to these tasks.
 - **Overall merit**: On a scale of 1 to 5, where 1 is strong reject and 5 is strong accept.
 - **Reviewer confidence**: On a scale of 1 to 3, where 1 is low and 3 is high (the reviewer completely understood the paper).
 - **Brief paper summary** (2-3 sentences): Summarizing the paper was indeed a good thing to practice how accurately we can describe the paper for others and present our understanding.
 - **Strengths**: We were told to look for good reasons to accept the paper, rather than finding reasons to reject. 
 - **Weaknesses**: All kinds of weaknesses such as theoretical/conceptual errors, narration and language were to be pointed out here briefly.
 - **Detailed comments for the author(s)**: I took special interest to write lengthy comments highlighting both strengths and weaknesses, as well as suggestions about improving the concepts within the paper. Out of all the papers I had recieved for reviweing, I could write good reviews ('good' according to me) for all but one paper. The one paper where I could not write a good review was too good, but too much outside my area of expertize.

 Out of 8 papers that were assigned to me, I had given 3 accept, 2 revise, 2 reject and 1 likely reject. This was based on on-line discussion with the other student PC reviwers who were assigned to each of those papers.


## 4. Final in-person meeting

Last but not the least part of the review process was the in-person meeting to vote for the papers that we reviewed so far and decide whether to *accept*, *reject*, *revise* or *shepherd accept*. This meeting was held in the Google New York office on Monday, 22nd January 2018. I got to meet my good old friend [Mahmood Sharif][sharif] (now a Ph.D candidate in CMU), whom I had met in 2014 in the [4th Bar-Ilan winter school on cryptography] which was held in Tel-aviv, Israel. Back then, we both were master students and had plans to pursue doctoral studies in the future. Look at us now! we both are pursuing our doctoral studies, part of the student PC committee, and also reviewed 2-3 same set of papers. I also got to meet some excellent Ph.D students from other universities.

![Me @ Google NY office]({{site.baseurl}}/assets/images/sid_google.jpg)
<p align="center">
    <em>Me @ Google NY office</em>
</p>

Most pf the student PC members (including the student PC chair - Prof. Thorsten) were gathered in a room for the round-table discussion. Each paper had one discussion lead (who is one of the reviewers), whose task was to summarize the paper for the audience, followed by collecting votes from other reviewers to decide whether to accept or reject/revise/sheperd accept the paper. In case of conflicts, the person who has the conflict has to leave the room until the discussion is over. 

This indeed was a tedious and never-ending task. It took the whole day to finish all the papers (i.e. ~80) which were to be reviewed by the student PC. 

![Me @ Google NY office]({{site.baseurl}}/assets/images/oakland_spc_meeting.jpg)
<p align="center">
    <em>Student PC meeting in the Google NY office</em>
</p>

After evertything was reviewed, Prof. Thorsten disclosed the comparison of our evaluation with the actual PC committee. The student PC was way too generous when it came to **revise**. Rest of the things were more or less close to the decision made by the actual PC. The below table summarizes the stats:

<table class="tablesaw tablesaw-stack" data-tablesaw-mode="stack" align="center" border="1">
    <tbody>
        <tr>
            <th colspan="1" rowspan="1">
                Evaluation
            </th>
            <th colspan="1" rowspan="1">
                Student PC
            </th>
            <th colspan="1" rowspan="1">
                Actual PC
            </th>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                Accept
            </td>
            <td colspan="1" rowspan="1">
            	12
            </td>
            <td colspan="1" rowspan="1">
            	5
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                Sheperd accept
            </td>
            <td colspan="1" rowspan="1">
            	4
            </td>
            <td colspan="1" rowspan="1">
            	3
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                Revise
            </td>
            <td colspan="1" rowspan="1">
            	10
            </td>
            <td colspan="1" rowspan="1">
            	3
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                Reject
            </td>
            <td colspan="1" rowspan="1">
            	78
            </td>
            <td colspan="1" rowspan="1">
            	91
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <b>Total</b>
            </td>
            <td colspan="2" rowspan="1"><b>104</b>
            </td>
            
        </tr>
    </tbody>
</table>


In short, this was a great experience and learning. Not only to feel how it feels to review other's work, but also to understand why and how our papers get rejected from elite conferences. Definitely, I would count this experience towards being a good academic in future.

[studentpc]: https://www.ieee-security.org/TC/SP2018/studentpc.html
[PETS]: https://petsymposium.org/
[NDSS]: https://www.internetsociety.org/events/ndss/
[thorsten]: http://www.syssec.rub.de/chair/staff/tho/
[instructions]: https://www.dropbox.com/s/x2cw90zgk4ymkq7/studentpc18-prereview.pdf?dl=0
[r1]: http://www.icir.org/mallman/pubs/All08a/All08a.pdf
[r2]: https://www.cs.utexas.edu/users/mckinley/notes/reviewing.html
[r3]: http://www.sigmod.org/publications/sigmod-record/0812/p100.open.cormode.pdf
[sharif]: https://users.ece.cmu.edu/~mahmoods/
[biu14]: https://cyber.biu.ac.il/event/the-4th-biu-winter-school/
