# PHOTOGRAPHY SPOT FINDER - NYC

This web application allows users to discover and share top photography locations in New York City and surrounding areas. Designed for both professional and amateur photographers, it helps users find the best spots for photo shoots, ranging from scenic spots and iconic landmarks to hidden gems. Users can browse locations, contribute their own, and interact with the community through comments and ratings.
Users can freely browse the site without the need to sign up. However, contributing photography spots, commenting, rating, and reporting photos require users to create an account.

## How to Setup

Step 1: Run `npm install` to install all the required dependencies of the project

Step 2: Run `npm run seed` to seed the Database (The Database's name is photography-spot-finder)

Step 3: Setup the `.env` file in the root directory with the following variables.

```
MAPBOX_API_TOKEN="api-key-here"
CLOUDINARY_API_KEY="api-key-here"
CLOUDINARY_API_SECRET="secret-here"
EMAIL_USER="email-here"
EMAIL_PASS="email-app-password-here"
```

Step 4: Finally, run the application using `npm start`. The application will run on port 3000 of the host machine.

**Note:** While testing our application, if you delete an asset that contains an image, we also **made sure it is deleted in the cloud** (for storage optimization and to prevent orphan images in the cloud). So, if you reseed the database using the seed command after deleting an asset with an image, the image will not be shown. Alternately, you can run `npm run export` to export your current database state and then run the seed command to reflect the deleted assets. We currently provided **enough seed data to test all aspects and features** but deleting an asset with an image will require adding more assets with images and then exporting the current database state to test them again.

**Admin credentials**:

- username: sivaanand
- password: Password@1234

## Core Features

1. **Landing Page:** Introduces the platform’s purpose and provides links to the top three rated photography spots of the month.

   - Features a prominent search bar allowing users to look up specific locations or by tag.
   - To qualify for the top-rated spots, a location must have at least five ratings and an average score of 7.5 or above (out of 10\) within the current month. If no spots meet this criterion, only the platform's purpose and search bar are displayed.
   - **Extra:** We also added a section that lists the current contest leaders.

2. **Spots List Page:** Displays a list of all photography spots on the platform. Users can filter spots based on timestamp, tags, ratings, or keywords.

3. **Photography Spot Submission:** Registered users can submit new photography spots, including

   - Spot Location (using an integrated map)
   - Description
   - Accessibility (public, restricted, free, paid, etc.)
   - Best photography times
   - Between 1 and 3 pictures of the spot
   - Up to five optional tags (e.g., cityscape, sunset, nature).

4. **Spot Detail Page:** Displays detailed information about each spot, including user-submitted photos, ratings, and tags.

   - Users can add their own photos of the spot
   - A comments section allows users to share experiences or tips
   - Users can rate spots on a scale of one to ten
   - Maps API Integration \- Integrates maps to show spot locations.

5. **Monthly Photo Contest:**

   - A monthly photo contest allows users to submit photos taken at featured spots (top 3 spots at the end of the previous month) \- users have a limit of three submissions
   - Other users can upvote or downvote photos to select the winners \- users only have one vote per photo (they can switch votes)
   - **Note:** The contest submission form uses AJAX

6. **User Profile Page:**

   - Users can modify their own profile (password, bio, etc.)
   - The user’s profile page includes all the spots, ratings, comments and contest submissions they have posted
   - Also includes Favorite Spots Section \- Users can save their favorite photography spots in their profile for easy access.
   - Users can modify or remove their spots, ratings, or comments from this page.

7. **Report Feature & Admin Panel:**
   - Users can report inappropriate content (limit of one report per item)
   - Admins can manage and moderate spots, comments, and contest submissions, with the ability to remove flagged content.
8. **Public Profile Page:** Displays a user’s bio, their favorite spots, submitted spots, comments and contest submissions.

## Extra Features

1. **Search Spots by Location:** Users can search spots near their physical location by providing a distance search radius and see interactively in a map all the spots around them. Users can then click on a spot marker to see a brief info regarding the spot and then access the full spot detail if they wish to do so.
2. **User Verification:** Perform user verification using verification link or OTP to verify user email address. The user’s public profile will then list them as verified. Editing/Removing the existing email will mark the user as `not verfied`.
3. **Search Users:** Visitors and existing users can search for other users by entering a name or username, and then visit their profiles directly from the results to have quick and easy access to a user’s submitted spots, comments, favorite spots, and contest submissions, instead of going to a spot detail page and then visiting a profile from there.

## Unit testing

We conducted unit testing using jest and have used a github workflow to create CI pipeline. You can run the tests using the command `npm run test`. This will empty the database, run the tests and then reseed the database.
