# Jobline's Problem

**Why focusing on UI can boost productivity!**

**Jobline is a simple app. Don’t overcomplicate it.**

**What is your organization VALUE STREAM**

Enterprise system is a complex, adaptive system. It cannot be understood by reductionism. One one single person can understand the whole system. It will have emergence behaviours. You cannot stop that behaviours.

> Today my Jawbone is a fairly basic data collection device. It knows that I walked 8,000 steps and slept too little, but it doesn't drive me to action other than providing me with a visualization of the data. In the Age of Context this will change, as larger and larger data sets of sensor data, combined with other data combined with intelligent analytics allows data to become actionable.

---
> The Twitter vs. Instagram experience is really reinforcing what matters when designing a product. What kind of behavior can we encourage? What kind of moments can we create for people? What do people anticipate before they use something? How does it leave them feeling when they’re done? These are now some of the most important questions for me when working on a design. - [Look and Feel and Feel](https://signalvnoise.com/posts/3868-look-and-feel-and-feel)

---
> We are unlikely to be able to sell "a group chat system" very well: there are just not enough people shopping for group chat system (and, as pointed out elsewhere, our current fax machine works fine) - [We don't sell saddles here](https://medium.com/@stewart/we-dont-sell-saddles-here-4c59524d650d)
> 
> The reason for saying we need to do 'an exceptional, near-perfect job of execution' is this: When you want something really bad, you will put up with a lot of flaws. But if you do not yet know you want something, your tolerance will be much lower. That's why it is especially important for us to build a beautiful, elegant and considerate piece of software. Every bit of grace, refinement, and thoughtfulness on our part will pull people along. Every petty irritation will stop them and give the impression that it is not worth it.
> 
> Be harsh, in the interest of being excellent.

* [Quip](https://quip.com)

## Normalised list of skill

If enough people add the same skill, we can normalize it. See https://vimeo.com/110012665

If CA1 is in the same school as CA2, compare and recommend the skills both have and prompt each to add to it.

## Main things, secondary thing

To Bob, the main thing is to take leave. To Alice, main thing is to keep track of payslip.

> Paving the cowpaths philosophy - we don’t like to tell you what to do, we like to find out what you’re doing, and then get the obstacles out of your way.

## Talent Networking

* [SAP Scouting](http://awards.ixda.org/entry/2014/sap-scouting/)

Social graph. 1 or more degree away from better referral.

Maintain good intel.

## Design for the moment

* [Moments as a currency](http://thenextweb.com/insider/2015/04/24/moments-as-a-currency-brian-wong-on-identifying-and-addressing-customers-needs-at-tnw-europe-conference/)

> One of the techniques that can be used to see customer's needs at specific moments (steps, stages) and at the same time to see the whole picture of their journey is Experience Mapping or Customer Journey Mapping.

## Microservices

Bounded Context - Identify discrete business capabilities (functions). Functions govern part of enterprise data model.

[The Scale Cube](http://microservices.io/articles/scalecube.html)

* Client API
* Talent API - Candidate, BIO, Resume/CV
* ATS API - Applicant, Application, Pipeline
* Billing API
* Employment API

Candidate in ATS bounded context is called Applicant. Don't ever create a God object for a single Candidate and try to write Applicant's behaviors in it.

Be smart about your boundaries. Boundaries are explicit. Bounded Context.

**1 week non-office remote days**

Sometimes SIMPLE really WINS.

There's a lot of challenges in crafting new experiences and workflows to meet contemporary HR demands.

---
> Some platforms may have users explicitly connecting with each other, as in social networks. Some may have users not connecting but exchanging items as in marketplaces. And some platforms may have an implicit community layer. E.g. If you use the Nest Thermostat or Mint.com, your usage is benchmarked against others. So you are benefiting from the community implicitly but you don’t explicitly connect with them.

---
> The final layer is the data layer. Every platform uses data in some way. But in some cases the data layer may play a more dominant role than in others. In most cases, data serves to provide relevance, matching the most relevant content/goods/services with the right users. In other cases, the value may exclusively lie in the data layer. The Nest Thermostat example, as we will revisit below, is what one would think of as a data-intensive platform, where the value is entirely in the data being aggregated with a minimal. - http://platformed.info/platform-stack/

---
> The Platform Stack is a tool for us to think through platforms and plan them. Irrespective of what you’re building, the stack helps to figure which layers you differentiate yourself in and how. It helps understand the key strengths of businesses that are already out there in the market. Without getting lost in the quagmire of features and functionalities, the stack helps us understand the key drivers of value and helps us benchmark ourselves on those parameters against competition and substitutes.

FitAgent, Fit4Hire, FitSense

* Track activities all around (See Atlassian Stash)
* The dashboard of CL is not very helpful in their day to day tasks, especially when it comes to month's end where they need to approve timesheets, leaves, etc. The level of audit and tracking is lacking also, such as who approve what, and when.
* CL really is confuse with the arrangement of what tasks they should do "right now", and how to keep track of what they have done.
* There is no way to know when Timesheet is being approved. Right now, I am using PostMark to see when email was sent to client to ask them to approved to determine Timesheet's submission date time.
* Creating timesheet is not idiot-proof. People can create Jan timesheet when it was Dec now! We must at least alert CA that Jan is not the correct month!
* Design staff on-boarding materials, like where to eat, etc.
* [Not just for HR and growth hackers](http://pjrvs.com/a/onboarding)
* Use [Moo.com](http://uk.moo.com/design-templates/luxe/business-cards/) for business card
* [Business cards](https://news.layervault.com/stories/32362-ask-dn-best-online-places-to-order-business-cards-from)
* Payslip - No date range select for like last 3 months payslip which is likely useful for many application requests.
* Import company members with update/merge. See Xero's CSV import example.
* Issues navigator - See Xcode 6 issues implementation. We can intelligently supply noted issues to recruiters.
* Make real-time per-event decision. See http://voltdb.com/welcome-1
* Make use of lots of popover for quick action
* Use Amazon SES for email blasting - See http://beta.emailoctopus.com/ also
* "Ready&Smile" - A slogan for interview
* Have a hello@jobline.com.sg email? For??
* [T-shaped skills](http://en.wikipedia.org/wiki/T-shaped_skills)
* [RightSignature](https://rightsignature.com/how-it-works/send)
* Company profile is crucial to attracting talents. We do not have a nice company profile that is compelling enough for CA to view.
* Company Ethos
* Some job categories are obsolete like "IT & Telecommunication"
* Let staff view their own job handling
* Scoreboards, leaderboards, let consultants see how they ranked among the entire community and adjust their strategy and velocity.
* SOA - some has partial payment and we can see the `amt_os` to know what is left for outstanding. I think only `nett_payable_w_gst` need to change to reflect the same as `amt_os` while `amt_payable_w_gst` remains.
* Display a "poo" besides those pipeline stages where it is long and smelly
* Scheduling interview - Missing CA at DB!
* Should we email CA when they
* [Invoice Me](http://invoiceto.me/)
* Have a web_db for Employer also so that we can track which employer has account already.
* Eliminate integration database or lessen its use
* Query visualiser - like "All active CLCT under CP_Main and CP_CC in all active SRID in the following CLID under Amy"
* Instead of requiring client to select their company if they have multiple companies, why not present all of it.
* Have data-structure to track verified NRIC, email, mobile phone (for SMS sending), etc.
* With each SMS being sent, we constantly see if the number is clean or not. Cross-associated SMS sent with the client/CA etc.
* Code Memo. Rules, etc. See MaxQDA. Code CA's resume? Like Medium website comment where you select/highlight chunk of text and mark it or comment on it.
* Separate cron jobs to a git **branch** and then deploy the cron jobs into another machine, different from the main operation machine.
* [Stiffer hiring checks to ensure right fit](http://news.asiaone.com/news/business/stiffer-hiring-checks-ensure-right-fit)
* [HireRight](http://www.hireright.com/)
* [See this login ideas](http://blog.codinghorror.com/the-god-login/)
* [The common password project](http://thepasswordproject.com/)
* [Create and share polls](https://github.com/daryl/qstn)
* When there is new staff, those with no StaffLeave entitlement or year specified cannot take unpaid leave. Maybe we need to be more up-front broadcasting system to May/Amy to prepare the setup first.
* ["Helping you DISCOVER a special thing: SELF"](http://joshsummers.co.uk/2015/02/16/Lego-1981-Beautiful-Advert/)
* For Timesheet, let CA opt-in to work on Public Holiday, instead of having them opt-out when they press the "default" hours to pre-filled the working hours.
* Case study for extensions. See Docker Machine's provider concept or Vagrant provider concept. If Jobline need any customisation for our customer, we can use such provider concept. Like Manpower Staffing cannot login, etc.. instead of hardcoding emails into the Dashboard controller.
* FileMaker log has device tracking, for web do we even know which devices tag to user account to check if they can access the content. For example the case with Andrew accessing FileMaker using Janna Rose's password. Do our web have such capability to track?

```
/cc @simon, @mech, @amy
```

```
(1 of 2378) -> too large? Narrow your search terms or use the filter
```

## Behavioural Design and Sociology Study

> Productivity failed to increase in step with increases in mechanization - Eric Trist (The Evolution of Socio-Technical Systems)

* Implement a streak workflow like the GitHub commit activities.
* Adaptive System
* The Bus Problem - some killed by a bus and you lost all the knowledge
* Constraints - TPC
* Resiliency
* Knowledge adjacency - you know what I do, I know what you do.
* Move to managing boundaries vs tasks! Don't tell people what to do, tell them the boundaries and the whole system views.
* If I tell you how to do it, the brain cannot scale.

## Data

* [How Big Data is Changing the Hiring Game](http://hirevue.com/blog/how-big-data-is-changing-the-hiring-game)
* [Everything we wish we'd known about building data products](http://firstround.com/review/everything-we-wish-wed-known-about-building-data-products/)
* [Why you need to embrace the big data trend in HR](http://www.entrepreneur.com/article/244326)
* [Hire better talent with a big data scientist](http://www.entrepreneur.com/article/235211)

> Deciding what data to expose to people isn't just about how much - it's about what it says too. One idea Patil and Belkin played around with was marketing jobs to people - like, "Hey, you should apply for this job because it matches your skills!" Soon, they realized this approach was fraught with peril.
> 
> "There was too high of a chance that we'd accidentally recommend a more senior person should apply for an internship, or that a confirmed California resident should move to Idaho for work. When stuff like that happens, people get pretty pissed off, and it can mess up your brand pretty fast," Patil says. "You have to think about what that particular feature will actually be like for a user when he or she sees it. This is where you need to be clever - and when it comes to data products, clever beats smart nine times out of ten."
> 
> The clever solution in this case was to approach job recommendations from a different angle. If "Bill" is the user they are trying to reach, then instead of sending recommended job openings directly to Bill, they decided to send them to his network with the short note: Recommend Bill for this job. It used the exact same algorithm, but with a little twist, it took care of the hard relevancy problems
> 
> "If Bill hears from one of his friends that they think he should take a job, he can still say, 'Yeah sure man, you're an asshole,' but that's rarer, and the site would never be blamed," Patil says. "Beyond that, we get to collect all the data that allows use to figure out what's going on with this feature and make it even better."

Business transaction data is well-understood and solve by SQL. Unstructured data like text, images and videos can't be solved by SQL.

Data analysis -> Break into group -> Targeted marketing (marketing as in the sense of value awareness)

Can you answer these questions:

* How many leaves requests you service for this month/year?
* How many timesheets Jobline process every months?
* Request flow (Twitter and Netflix)

Check out histogram so as not to skew data reading.

## Pipelines

```
Sources -> Filters -> Sinks
(CA/JD) -> ATS     -> Hired/Rejected
```

## Redis

For payslip, past timesheet, anything that involved past records, we tried to cache it at the Redis level for fast access or just to make FileMaker less load.

Even if we nuke the Redis, we can still populate it upon as people request the resources.

We can key the payslip quarter by quarter. So we pulled down 3 months worth of payslip and it's JSON representation to the Redis server and never has to bother asking FM again.

## Storage

Make use of Amazon S3 as much as possible. For simple invoice file caching, or resume caching, we can use S3, etc.

## SMS

Our current SMS reply is not scalable with `Reply 'JL @35845' followed by your message to 8100382`. We should use `@r1` or `@m1` to represent recruit1 and msd1 and then link the phone number to form a nice conversation flow.

Track how many SMS being sent per day, then we can make more decision on usage:

```
SmsMessage.where(created_at: Date.new(2014,11,21).beginning_of_day .. Date.new(2014,11,21).end_of_day).count
```

Support for Emoji needs utf8mb4. Or just use Postgres.

* If failed to send SMS, notify also to the consultant so they can act on it, rather than email only to IT for `DeliveryImpossible`.
* [Rails 4.1 and MySQL 5.5 support utf8mb4](http://tech.taskrabbit.com/blog/2014/04/24/active-record-mysql-and-emoji/)
* [Unicode support in MySQL is...](http://www.codeka.com.au/blog/2014/02/unicode-support-in-mysql-is--)

## Customer Development

Be it customer service.

Make our customer our evangelist.

Have you ever spend any time with customer?

This is FALSE: "Customer aren't using things the way we designed them"

Who "owns" the customer relationship? The Account Manager? Sales?

Have a concept of a "Account Holder" and their own CRM.

## Accrual

INR accrual can only have all same `work_year`.
@mech - not sure what this meant, but must be something to do with Xero accrual import on that year where work_year is not the same.

## Timesheet

Have option that allow CA to indicate that TS should follow the previous month values. Sort of like how IRAS file your income tax. It will be automatic if you do not have any new things to add/change.

Send an email that says "We noticed for the past 3 months your TS hours are the same, we can auto-submit for you if you are sure you never change your TS."

Remove NRIC on TS PDF.

**Timesheet and leaves and a reactive system**

What happen when timesheet was submitted for pending approval and CA take leaves? Approver should get alert/warning that there is pending leaves being add on to a populated timesheet day's hours. If the leave is approved on that day, the timesheet must null out all the hours and reflect the new total hours being logged. **Make it reactive!**

---

When email for timesheet approval, we can show the overall total-hour taken by each candidates.

If there is only 1 candidate to approve, we can show all the details in the email and one "Approve" button which will approve without requiring them to login, or login automatically.

## Change of Approver

If approver for a certain SRID or project has been made, all pending leaves, timesheet, etc need to be updated to the new approver. Any email for the pending items need to be resend so the "new" approver will know to act on it.

## Pub/Sub

If someone is interested in some event, we can broadcast to them.

Publish conclusion.

## PDF

* [jsPDF](https://parall.ax/products/jspdf)
* [PanDoc](http://johnmacfarlane.net/pandoc/)
* [PDF Viewing in GitHub](https://github.com/blog/1974-pdf-viewing)
* [**PDF.js**](https://github.com/mozilla/pdf.js)
* [HTML to PDF](https://www.designernews.co/stories/51286-html-to-pdf)

## Email

* [POP in iPhone](http://support.apple.com/en-sg/HT201855)
* [POP vs IMAP](http://www.pop2imap.com/)

We send reminder to approve timesheets for client (approver) and list down the candidate names. If they are like Chris Goh who need to approve 47 candidates, and he only approve 20, our next email reminder will "encourage" him to close it in the last mile by introducing some cute animation? characters? Or we can show checkboxes where those approved candidates will get checked or strike off to let him know he is so close to approving for all.

## Account Management

* Invitation (invite collaborator, co-worker, etc. See Dropbox example - https://www.dropbox.com/guide/business/highlights/getting-started)
* Transfer Ownership
* See Amazon AWS's IAM policy like Allow, Deny as example. Groups.
* Users, Groups, Roles, Permissions, Sharing, Conditions

Use Group to manage Permission. Don't manage it at User-level.
Map permissions to a specific business function.

---

* Should we email CA when they are CV profiled - Eveleen
* Schedule Interview - What happen if the CA is not in our DB? Should we import them even if they don't have SRID with us.

## Privacy and Security

* Your JSON data cannot be Google searchable. See robot.txt
* 

## NRIC

* http://www.arjun.com.np/blog/all-about-nric-number-in-singapore/
* http://www.wikiwand.com/en/National_Registration_Identity_Card
* http://gangasudhan.com/blog/2008/07/nric-fin-number-suffix-checker.html
* 


Histograms
Sparklines