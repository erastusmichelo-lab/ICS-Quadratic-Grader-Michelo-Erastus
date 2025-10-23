# ICS-Quadratic-Grader-Michelo-Erastus
Program takes 3 integer values (a, b and c) and  calculates the two possible quadratic values of x. The program also accepts numerical Values between 0 and 100 and generates a grade accordingly.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quadratic Calculator</title>
</head>
<body>
        
        <h2>Quadratic Equation Solver</h2>
                                                                <!-- Quadratic Equation Input fields -->
        <input type="number" id="a" placeholder="a">
        <input type="number" id="b" placeholder="b">
        <input type="number" id="c" placeholder="c">
                                                                <!-- Submition button -->
        <button onclick="SolveEquation()">Solve</button>

        <div id="results"></div>
                                                                <!-- Grading system ...Input Field-->
        <input type="number"
                id="gradeScore"
                min="0" 
                placeholder="Enter your grade">

        <input type="submit"
                id="checkGrade" 
                value="Check Grade"
                onclick="runValue()">

        <div id="gradeResults"></div>

    <script>
                                                                //Getting value from input fields and assigning constant variables
        function SolveEquation() {
            const a = parseFloat(document.getElementById('a').value);
            const b = parseFloat(document.getElementById('b').value);
            const c = parseFloat(document.getElementById('c').value);

            const resultsDiv = document.getElementById('results');
            resultsDiv.innerHTML = '';                             //Clearing previous results

                                                                //Checking for valid inputs
            if (isNaN(a) || isNaN(b) || isNaN(c)) {                 
                resultsDiv.innerHTML = 'Please enter valid numbers for a, b, and c.';
                return;
            }
                                                                //Handling linear case when a = 0
            if (a === 0) {
                if (b === 0) {
                    resultsDiv.innerHTML = c === 0 ? 'Infinite solutions' : 'No solution';
                } else {
                    const root = -c / b;
                    resultsDiv.innerHTML = `Linear equation root: x = ${root}`;
                }
                return;
            }
                                                                //Calculating discriminant
            const discriminant = b * b - 4 * a * c;

            if (discriminant > 0) {
                const root1 = (-b + Math.sqrt(discriminant)) / (2 * a);
                const root2 = (-b - Math.sqrt(discriminant)) / (2 * a);
                resultsDiv.innerHTML = `Two real roots: x1 = ${root1}, x2 = ${root2}`;
            } else if (discriminant === 0) {
                const root = -b / (2 * a);
                resultsDiv.innerHTML = `One real root: x = ${root}`;
            } else {
                resultsDiv.innerHTML = 'No real roots';
            }
        }
                                                                //Grading system function
        function runValue(){

            const gradeScore = parseFloat(document.getElementById('gradeScore').value);
            const gradeResultsDiv = document.getElementById('gradeResults');
            gradeResultsDiv.innerHTML = '';                         //Clearing previous results

                                                                //Checking for valid input
            if (isNaN(gradeScore) || gradeScore < 0 || gradeScore > 100) {
                gradeResultsDiv.innerHTML = 'Enter a valid grade between 0 and 100.';
                return;
            }

            let grade;

            if (gradeScore >= 85 && gradeScore <= 100) {
                grade = 'A+';
            } else if (gradeScore >=75 && gradeScore <=84 ) {
                grade = 'A';
            } else if (gradeScore >= 65 && gradeScore <=74) {
                grade = 'B+';
            } else if (gradeScore >= 60 && gradeScore <= 64) {
                grade = 'B';
            } else if (gradeScore >= 55 && gradeScore <= 59) {
                grade = 'C+';
            } else if (gradeScore >= 50 && gradeScore <= 54) {
                grade = 'C';
            } else {
                grade = 'D';
            }

            gradeResultsDiv.innerHTML = `Your grade is: ${grade}`;

        }

    </script>
</body>
</html>
