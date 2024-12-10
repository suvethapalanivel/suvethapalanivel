from flask import Flask, render_template, request

# Initialize the Flask app
app = Flask(__name__)

# Route for the home page
@app.route('/')
def home():
    return "<h1>Welcome to My First Web App</h1>"

# Route to display a form
@app.route('/form')
def form():
    return '''
        <form action="/submit" method="post">
            <label for="name">Name:</label>
            <input type="text" id="name" name="name"><br><br>
            <input type="submit" value="Submit">
        </form>
    '''

# Route to handle form submission
@app.route('/submit', methods=['POST'])
def submit():
    name = request.form.get('name')
    return f"<h1>Hello, {name}!</h1>"

# Run the application
if __name__ == "__main__":
    app.run(debug=True)
