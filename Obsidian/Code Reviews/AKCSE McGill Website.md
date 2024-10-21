> Mostly my thoughts on the website. Please only take what's important as feedback, because I'm mostly just saying things that pop up in my head as I scan through the website. I'm not a real front-end engineer or anything, just a visitor paying a visit :) 

> I can also miss a bunch of things! I highly encourage finding a friend that can also look at the website in more detail as well. 
## Idea
- Future members can contribute
	- Currently 3 people contribute
	- Needs to be open source and modular
	- Repository needs to be set up with proper CI/CD to save the website from crashing / bugs making it to prod
	- Needs to have proper review team to check pull requests to stop bad merges
	- Needs to have a good workflow to avoid merge conflicts
## Website
### Desktop View
- Components
	- Issue: Navbar's page-redirect buttons are not centered
		- Easy to tell when you go to the `/'about` page and see the misalignment compared to the `What is AKCSE` hero banner text.
	- Footer
		- The phrase `2024 AKCSE McGill Executives`
			- Executives are copyrighted?
			- Is AKCSE McGill copyrighted?
			- Or is it just AKCSE that's copyrighted?
- Main page
	- Issue: Three.js fragment is filled-to-fit - which breaks on ultrawide monitors
	- Will this need to change to work with the "members can contribute" idea?
	- 
- About
	- AKCSE slider
		- Issue: When you double-click on one of the buttons, the slide-in component will disappear
		- Issue: There is a misspelling in the hero banner: `ACKSE` instead of `AKCSE`
		- Nit: Needless comma between `provinces of Canada, with its headquarters...`.
		- Nit: `The chapters are divided based on different stages in one's career` is a bit hard to read at first - is it clearer to say "students" or generalize to "person" instead of "one"?
		- Q: Is the "Local chapter" also a "stage" or is it more of a group that contains those stages? If it's the latter, then the phrase `... the ..(YG),..(YP), and the local chapter` is not correctly grouped. It's probably better to separate those or make it more distinct.
		- Nit: `The Ministry of Science` is `The` also a part of the proper noun? If not, then we need to lowercase it.
		- Q: `... and ICT of the Korean Government` what's the ICT?
		- Nit: Double `and`s in sentence `AKCSE is affiliated with The Ministry of Science and ICT of the Korean Government, the Korean Federation of Science & Technology Societies, and many different organizations.`
		- Preference: Since you've already used `Scholarship` in the sentence, maybe it's better to use `award` for the second duplicate. E.g. `Additionally, students can apply for the KCSSF Scholarship, granding 12 students the award valued up to $3,000`.
			- What's the KCSSF Scholarship?
				- What does it stand for?
		- Preference: Is it better to leave the AKCSE's slide-in description as part of the page, statically placed (instead of the current format, idk somewhere in the hero banner or directly under it as a quoted block) so they can always view it in the `/about` page, so the readability and the understanding of AKCSE increases because readers can more easily go back on what the organization does when scanning through the branched `Young Generation`, `Young Professionals`, and `Local Chapter` buttons?
			- Also the `Official Website` seems to come up a lot (AKCSE, Young Generation, and Young Professional slide-ins). Is it better to statically place them somewhere in the hero or right below the sliding panels or in the footer area?
	- Young Generation slider
		- nit: `Through activities like orientation, seminars and hackathons` (oxford comma is missing)
		- nit: Needless comma between `amongst scientists, and build a connection`.
		- nit: `at McGill` instead of `in McGill`.
		- Says `YG School Chapter in AKCSE`, but in Young Professionals it says `Young Professionals in AKCSE`. Don't know if it's intended!
	- Young Professionals slider
		- Different spellings of Quebec (sometimes it has an accented é, sometimes it does not!)
		- Nit: Needless comma between `to colalborate, and share their...`
		- Nit: Missing fullstop period at the end of the first paragraph.
	- Local chapter slider
		- Nit: Needless comma between `join AKCSE, regardless of their...`
		- Q: Is it better to say "Young Professionals" instead of "Professionals in their early career stages" because we've already defined it in one of the sliders?
		- Nit: Needless comma between `each other, as well as with...`.
- Events
	- Images are a bit low-quality. Unsure if it's just the picture that's small 
- Executives
- Projects
### Mobile View
# Devops