pipeline{
	agent none 

parameters{
	string(name:'ENV', defaultValue:'Test',description:'This is for the test')
	booleanParam(name: 'executevalue', defaultValue: true, description: 'decided to run for the Test')
	choice(name: 'APPVER', choices: ['1.3', '1.4', '1.5'], description: 'This is the app version')  
}

stages{
	stage(compile){
		agent any
		echo "This is the compile stage ${params.ENV}"
		sh "mvn compile"
	}
}

}