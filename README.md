# EMS
- EMS Git Repository info

	-> Executable: EMS-0.0.1.jar file to start the EMS backend application.

	-> Executable: EMS-FE folder to start EMS user interface.

	-> Sources: source/EMS_Backend/EMS Java application source code.

	-> Sources: source/EMS_FE React application source code.

 

-  Prerequisites:

   -> Java1.8 installed on the machine[Not tested with other versions].

 
- Installation instructions

   -> Copy executables/EMS-0.0.1.jar file.

   -> Open command prompt/terminal , goto the jar file location and run command "java -jar EMS-0.0.1.jar"

   -> The application starts on port 8585, please check console if any errors.
   
   -> Open URL localhost:8585/swagger-ui.html in browser and check Swagger-UI is rendered.

   -> copy executables/EMS-FE folder and open index.html in a browser.

                              

- Operational instructions

	   -> open http://localhost:8585/swagger-ui.html in browser(Chrome is recommended). The swagger front-end should be loaded if all fine. If not please check trobleshooting instructions.

	   -> Login using Employee controller -> login , with admin1/admin1 [copy sample request json and replace json params]. If login is succesfull, access token is returned. use this access token as a header in the next consecutive requests. Note: when the server is restarted, new access token will be generated by logging in again.

	   -> The login convention is adminX/adminX where X is the company ID. the access token is X.random number. Login is possible upto admin1000 , however create the company to start adding employees.By default one company with ID=1 is created on startup and one employee is present in the company. Recommended to start with admin1/admin1 to understand the default behavior.

	   -> To check the inmemory H2 database open URL, http://localhost:8585/h2_console  with datasource URL:jdbc:h2:mem:EMS_DS, username:admin, password:admin

	  

		- Front-end usage instructions
	   
		   -> Open index.html in browser.

		   -> login with user id for example admin1/admin1

		   -> The employee list is populated. Employee can be deleted with X link.

		   -> Create an employee with create employee widget.

		   -> To test with different companies , use Swagger to create company first, Front-end does not provide facility to manage companies.
		   
- Trouble shooting instructions

	EMS Backend:

	   -> During the jar execution, please check port 8585 is not occupied by any other application.

	   -> Please check installed java version by executing command java -version and check Java8 is present.

	EMS Frontned:

	   -> Check npm version.

	   -> Check access token is sent correctly in the header if 401/403 is returned by service.

                              

- Code setup and walkthrough

	EMS Backend:

	   -> The application is developed using Spring boot version 1.5.9.RELEASE and using IDE STS.

	   -> Application.properties file has tomcat port and H2 configuration settings.

	   -> data.sql contains the default queries to run during the application startup.

	   -> Authentication is done via inbuilt access token logic to simplify the authentication logic. Token = $compnayId.randomNumber, refer to Constants.java for more info.
	   
	   -> JPA CRUD repository is used for database itegration.



	EMS Frontend:

	   -> Prerequisites: npm

	   -> The front-end is developed using React JS, version 16.2.0 using IDE Visual Studio Code.

	   -> Copy source files into a folder and open the folder in the editor.

	   -> Navigate to the folder and run "npm start"  

