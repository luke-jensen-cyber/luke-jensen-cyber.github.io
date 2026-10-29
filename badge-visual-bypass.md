# Physical Security: ID Badge Visual Bypass

**Date:** October 2026

**Security Domain:** Physical Security / Social Engineering

**Tools Used:** Claude (AI), Python with OpenCV, HTML/SVG, Orbitron font (Google Fonts), Fargo DTC4000e card printer
---

## 1. Scenario & Objective
A student posted a "First Day!" photo on social media with their access badge sitting on a counter in the background. Acting as a red team operator with no access to card cloning hardware, my goal was to recreate the badge with my own name and photo from that one photo, closely enough that it could pass a quick visual check next to the real badge.

## 2. Architecture & Design
<img width="320" height="507" alt="Luke-Jensen-badge" src="https://github.com/user-attachments/assets/d98c8db5-1fac-40a4-9c4e-3ac243097c24" />

*My finished badge, rebuilt at the standard ID card size of 2.13" x 3.38".*

## 3. Methodology & Execution
1. **Extraction:** The badge in the photo was small and photographed at an angle, so I used a perspective warp to flatten it into a straight-on rectangle. From there I could read the layout, the text, and the colors.
2. **Rebuilding instead of cleaning:** Instead of trying to remove the glare and shadows from a blurry photo, I rebuilt every element from scratch (the header stripes, photo frame, circuit-line pattern, and text) so the final card looks like an original digital design, not a photo of a card.
3. **Matching the details:** I compared about 30 fonts against the original lettering and matched it to Orbitron. I traced the faint circuit lines on the sides by boosting the photo's contrast until they showed up, then redrew them in the same positions.
4. **Validation:** I overlaid my version on the original and adjusted until the stripes, frame, and text lined up within a few pixels. I also checked that the final file was exactly 2.13" x 3.38" so it would print correctly on the card printer.

## 4. Challenges & Troubleshooting
* **Issue Encountered:** The first cutout of my headshot clipped parts of my hair, my ear, and my shirt collar.
* **Troubleshooting Steps:** I zoomed in on each edge and found the background wall was close to my skin color, so the cutout couldn't tell them apart.
* **Resolution:** I separated skin from wall by color in those areas and redid the edges until my full outline was intact.

* **Issue Encountered:** Microsoft Edge reported the PDF as 2.83" x 4.50" instead of 2.13" x 3.38".
* **Troubleshooting Steps:** I checked the file's actual page size and tested Edge with a standard 8.5" x 11" page.
* **Resolution:** The file was correct; Edge was misreporting the size. I confirmed it using the PNG's properties (639 x 1014 pixels at 300 dpi).

## 5. Conclusion & Lessons Learned
**Final Outcome:** I produced a print-ready badge with my name and photo that matches the original's layout, font, and design closely enough to pass a quick visual inspection.

* **Lessons Learned:** One casual photo can leak enough information to copy a badge. Most of the work was in the small details, like font, spacing, and faint background patterns, since those are what make a fake stand out.
* **Security Recommendations:** Never post photos that show access badges. Organizations should use badges that can't be verified just by looking at them (smart cards or badge readers at every door), add security features like holograms, and train staff not to wave someone through based on a badge alone.
