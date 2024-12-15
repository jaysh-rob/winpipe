pipeline{
	agent none 

parameters{
	string(name:'ENV', defaultValue:'Test',description:'This is for the test')
	booleanParam(name: 'executevalue', defaultValue: true, description: 'decided to run for the Test')
	choice(name: 'APPVER', choices: ['1.3', '1.4', '1.5'], description: 'This is the app version')  
}

stages{
	stage('compile'){
		agent any
		echo "This is the compile stage ${params.ENV}"
		sh "mvn compile"
	}
}

stage('test'){
	when{
		expression{
			params.executevalue == True 
		}
	}
	agent any 
steps{
	echo "This is the Testing"
	sh "mvn test"
}
Post{ 
	always{
		junit 'target/surefire-reports/*.xml'
    }
}

}

stage('package'){
	when{
		expression{
			BRNACH_NAME == "feature"

		}
	}
}

input{
	message "Select the version which you want to deploy"
	ok "Version selected"
	parameters{
		choice(name:'APPVERSION', choices:['1.5', '2.5', '3.5'])
	}
}

steps{
	echo "package the code ${params.APPVERSION}"
	sh "mvn package"
}

}