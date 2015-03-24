# Jobline's Problem

**Jobline is a simple app. Don’t overcomplicate it.**

Enterprise system is a complex, adaptive system. It cannot be understood by reductionism. One one single person can understand the whole system. It will have emergence behaviours. You cannot stop that behaviours.

> Today my Jawbone is a fairly basic data collection device. It knows that I walked 8,000 steps and slept too little, but it doesn't drive me to action other than providing me with a visualization of the data. In the Age of Context this will change, as larger and larger data sets of sensor data, combined with other data combined with intelligent analytics allows data to become actionable.

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

Data analysis -> Break into group -> Targeted marketing (marketing as in the sense of value awareness)

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

## Pub/Sub

If someone is interested in some event, we can broadcast to them.

Publish conclusion.

## PDF

* [jsPDF](https://parall.ax/products/jspdf)
* [PanDoc](http://johnmacfarlane.net/pandoc/)

## Email

* [POP in iPhone](http://support.apple.com/en-sg/HT201855)
* [POP vs IMAP](http://www.pop2imap.com/)

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