import dash
import dash_core_components as dcc
import dash_html_components as html
import pyvisa
rm = pyvisa.ResourceManager()
rm.list_resources()
('ASRL1::INSTR', 'ASRL2::INSTR', 'GPIB0::22::INSTR')
inst = rm.open_resource('GPIB0::22::INSTR')

lst = []
nu=[]
n = 6
for i in range(0, n):
    ele = inst.query("MEASure:VOLTage:DC?")

    lst.append(ele) # adding the element
    nu.append(i)
external_stylesheets = ['https://codepen.io/chriddyp/pen/bWLwgP.css']

app = dash.Dash(__name__, external_stylesheets=external_stylesheets)

app.layout = html.Div(children=[
    html.H1(children='Hello Dash'),

    html.Div(children='''
        Dash: A web application framework for Python.
    '''),

    dcc.Graph(
        id='example-graph',
        figure={
            'data': [
                {'x': nu, 'y': lst, 'type': 'line', 'name': 'SF'},
            ],
            'layout': {
                'title': 'Dash Data Visualization'
            }
        }
    )
])

if __name__ == '__main__':
    app.run_server(debug=True)
