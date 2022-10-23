# masa-exam

## Part I: Theory

_Please, do NOT use online resources as an assistance for this part of the exam_

## Section A: Please, select the correct answer or the most close to the correct one _=> 20 points:_

1. **What is a PR?** _=> 2 points_

- [ ] Program Result: the outcome of a programming effort available for testing
- [ ] Public Relations: a practice of managing and influencing an organizational info to the public
- [x] Pull Request: a request to review the code of a developer prior to merging it main branch
- [ ] Private Role: A security role that is used in internal system processing

2. **What is the role of a service in nodejs server architecture?** _=> 2 points_

- [ ] Get the request from the router, treat the request parameters, prepare the response of the server to the consumer
- [x] Keep state of a specific logic portion of the system, provide processing of the data passed from the different controllers, parse the data and returned the processed response
- [ ] To be the first element in the system that should service the consumer for his CRUD request to the server
- [ ] To provide services to the system that do not require a state but should be used across the whole system

3. **What is INNER JOIN?** _=> 2 points_

- [x] A mechanism to link between to tables in the SQL query to bring data based on the same value in two tables. Allows NULL values on one on the sides of the JOIN
- [ ] A mechanism to link between to tables in the SQL query to bring data based on the same value in two tables. Only non NULL values are accepted for both sides of the JOIN
- [ ] A way of executing to `foreach` loops in JS/TS while the internal loop uses values of the external loop
- [ ] Such a term does not exist

4. **What is the code of a server error in HTTP protocol?** _=> 2 points_

- [ ] 2xx
- [ ] 3xx
- [ ] 4xx
- [x] 5xx

5. **What is the correct flow a story?** _=> 2 points_

- [ ] Software Detailed Design (SDD), Product design, QA review, UI design, Development, QA testing, Customer review
- [x] Customer request, Product design, UI design, SDD, QA review, Development, QA testing, Customer User Acceptance Testing (UAT)
- [ ] Product design, SDD, QA review, UI design, Development, QA testing, UAT
- [ ] Customer request, UI design, Product design, UAT, QA review, Development, QA testing

6. **Which tool would you use to test a nodejs server?** _=> 2 points_

- [ ] Browser
- [x] Postman
- [ ] Fiddler
- [ ] All answers are correct

7. **What is the most secure way to connect to SQL Server?** _=> 2 points_

- [ ] Integrated security
- [ ] Mixed mode
- [x] SQL Server login
- [ ] Application role

8. **What is the correct pair of a protocol and the port for secure HTTP communication?** _=> 2 points_

- [ ] HTTP:80
- [ ] HTTPS:80
- [x] HTTPS:443
- [ ] HTTP:443

9. **What is a trigger?** _=> 2 points_

- [x] Trigger is a piece of code executed by the database engine whenever some action is performed on a database object like tables, view, etc.
- [ ] Trigger is a method that is called JS/TS environment whenever a certain event is fired to complete an asynchronous code execution
- [ ] Trigger is a processing being performed right after the merge of a code to main branch in order to run a build for the system
- [ ] Trigger is the mechanism by which the router is sending its data to the controller in nodejs server

10. **Why would you use the JWT token? (more than a single answer can be selected)** _=> 2 points_

- [x] JWT tokens are encrypted
- [ ] It's a more secure way of handling authentication and authorization data than username and password
- [x] JWT tokens are signed and this signature can be verified uniquely
- [ ] All answers are correct

## Section B: Please, explain the following terms the best way you can _=> 22 points_

11. **Authentication & Authorization** _=> 7 points_
    Authentication is a method to check that user with definite login and password is in the DB.

Authorization is the method to define user's rights accodding to his role in the system.

12. **Stored procedure** _=> 3 points_

It is a kind of querry to the DB witch is stored on the server. Has one or more operators transact-sql. We can call SP with its name in the code.

13. **Git rebase** _=> 4 points_

It is useful way to move your commits to the more general branch. Your commits goes to the head of branch.

14. **Generics** _=> 4 points_

It is a way to use different types in Typescript. They are used for describe close but having some differences types.

15. **Middleware** _=> 4 points_

It is a kind of method that handles some logic in the middle of the process. Then it transfer data to the next function or makes some kind of reject.
For example it can be used in authorization and verify a role of the user.

## Part II: Practice on paper _=> 45 points_

_No restrictions on online resources usage. You also may use your development machine for assistance in debugging if needed._

16. **You received a bug stating the following: "Intermittently the following method results in a system getting stuck." You're required to find and fix the problem in this method:** _=> 10 points_

        public static addMonths(date: Date, value: number): Date {
            let expectedMonth: number = date.getMonth() + value;
            if (expectedMonth > 12) {
                expectedMonth = expectedMonth % 12;
            }

            if (expectedMonth < 0) {
                expectedMonth += 12;
            }

            date.setMonth(date.getMonth() + value);
            const daysToAdd: number = date.getMonth() >  expectedMonth ? -1 : 1;
            while (date.getMonth() !== expectedMonth) {
                date.setDate(date.getDate() + daysToAdd);
            }

            return  date;
        }

17. **Having the following DB tables diagram:** _=> 10 points_

![](https://github.com/lentyaishe/masa-exam/blob/dev/resources/db-relations.jpg)

You need to write a query that returns for each student his/her parents' information/ Take into consideration that the amount of parents for the child can be different ("Orphan" comment should appear for any child that has no parents defined in the tables). The data should be returned in the following manner:

| Student         | Parents                                      |
| --------------- | -------------------------------------------- |
| John Doe        | Mark Doe (09-1231231), Jane Doe (09-4132123) |
| Mary Smith      | Klark Smith (07-2134897)                     |
| Patrice Raymond | Orphan                                       |

18. **Write a method in JS/TS that gets as an argument an array of numbers and returns the sum of all array members**. _=> 5 points_

19. **Explain the following piece of code:** _=> 5 points_

        public static padLeft(input: number, places: number): string {
        	const zeroes: number = places - input.toString().length + 1;
        	return Array(+(zeroes > 0 && zeroes)).join("0") + input.toString();
        }

20. **Fix the following code and fill the required gaps in it by the coding standards. The purpose of this code is to verify the user is a member of a specific role and in case the user is the user data is returned by the isUserPermitted() method. Treat the comments as actual code written that should not be changed:** _=> 15 points_

        interface user {
        	id: number;
        	firstName: string;
        	lastName: string;
        }

        interface dbUser {
        	id: number;
        	first_name: string;
        	last_name: string;
        }

        interface role {
        	id: number;
        	userIds: number[];
        }

        interface dbRole {
        	id: number;
        	user_id: number;
        }

        public isUserPermitted(userId: number, roleId: number): Promise<user> {
        	return new Promise<user>((resolve, reject) => {
        		Promise.all([
        			this.getUser(userId),
        			this.getRole(roleId)
        		])
        		.then((results: [user | role]) => {
        			return results[1].userIds.indexOf(results[0].id) > -1;
        			resolve(results[0]);
        		});
        	});
        }

        private getUser(userId: number): Promise<user> {
        	return new Promise<user>((resolve, reject) => {
        		// Access to the DB that returns the user data by id as dbUser or null
        	});
        }

        private getRole(roleId: number): Promise<role> {
        	return new Promise<user>((resolve, reject) => {
        		// Access to the DB that returns the role data by id as array of dbRole or null
        	});
        }

## Part III: Practice on dev machine _=> 33 points_

_No restrictions on online resources usage_

- Clone the repository: https://github.com/lentyaishe/masa-exam;
- Switch to `broken-server` branch;
- Create a new git repository under your personal Github called `masa-exam`;
- Load the `main` branch of your new repository with the contents of the `broken-server` branch;
- Each bug in the list should be solved in designated branch.

The following is the list of currently existing problems with the system. :

21. **The server solution cannot be compiled. Fix all compilation issues accordingly.** _=> 10 points_

22. **An attempt to get a list of board types fails.** _=> 5 points_

23. **Any request to the server returns: "A token is required for authentication" even in case the token is supplied for the request.** _=> 5 points_

24. **Addition of the new user cannot be performed. Returned error message: "Incorrect query".** _=> 5 points_

25. **On an attempt to add a new board type an error: "not found" is returned.** _=> 8 points_

# Good luck!!
