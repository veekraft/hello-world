import os
import uuid
from flask import Flask

app = Flask(__name__)
my_uuid = str(uuid.uuid1())
BLUE = "#777799"
GREEN = "#99CC99"
YELLOW = "#FFFF00"

COLOR = GREEN
COLOR2 = YELLOW

@app.route('/')
def mainmenu():

    begin_html = """
    <html>
    <head>
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <!-- Latest compiled and minified CSS -->
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.0/css/bootstrap.min.css">
    </head>"""
    end_html = "</body></html>"


    agenda_html = """
    <link rel="stylesheet" type="text/css" href="mystyle.css">
    <body bgcolor="{}">
      <p><img src="static/agenda_icon.png" width="120" height="120" alt="Event Agenda"><h1><u>Event Agenda</u></h1></p>

      <table>
        
        <th>Session Time</th><th><Session Description</th>
        <tr>  
          <td>09:00</td><td>The wonderful world of Cloud Native</td>
        <tr>
          <td>10:00</td><td>DevOps demystified</td>
        <tr>
          <td>11:00</td><td>Agile for Dummies</td>
      </table>

    """.format(COLOR)

    guid_html = """
    <center><h1><font color="white">Hi, I'm GUID:<br/>
    {}</br>

    </center>

    """.format(COLOR,my_uuid,)

    floorplan_html = """
    <a href="floorplan.html">Show floor plan</a>

        
    """.format(COLOR)

## This is our python code in mainmenu():
    f = open("sessions.txt","r")
    session_list = f.readlines()
    f.close() 

    session_info = []
    for each_session in session_list:
        ##print each_session
        session_info = each_session.split(',')
        print "Session id  : " + session_info[0]
        print "Title       : " + session_info[1]
        print "Starts at   : " + session_info[2]
        print "Presenter   : " + session_info[3]
        print "Description : " + session_info[4]
## End python code in mainmenu()
  
    end_html = "</body></html>"
    
    response = begin_html + agenda_html + guid_html + floorplan_html + end_html

    return response

@app.route('/floorplan.html')
def floorplan():

    return """
    <html>
    <body bgcolor="{}">

    <img src="/static/floorplan.jpg">
    <a href="/"><u>Main Menu</u></a>
    </body>
    </html>
    """.format(COLOR2,my_uuid,)
        
if __name__ == "__main__":
	app.run(debug=False,host='0.0.0.0', port=int(os.getenv('PORT', '5000')))
