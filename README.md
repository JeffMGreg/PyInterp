QIPythonWidget
==============

Embedded python interpreter for PyQt4/PySide using the IPython project.
Tested with python 2.7 and IPython 0.13.1

This was build from a stackoverflow <a href="http://stackoverflow.com/questions/11513132/embedding-ipython-qt-console-in-a-pyqt-application">question</a>

## Example

```python
from PySide.QtGui  import *
from QIPythonWidget import QIPythonWidget

class Main(QWidget):

    def __init__(self, parent=None):
        super(Main, self).__init__(parent)
        layout = QVBoxLayout(self)

        self.button = QPushButton('Another widget')

        # Just like any other widget
        self.iPython = QIPythonWidget()

        layout.addWidget(self.button)
        layout.addWidget(self.iPython)


app  = QApplication([])
main = Main()

# assigen vars to user namespace
namespace = main.iPython.get_user_namespace()
namespace['main']    = main
namespace['foobar']  = 'value for foobar'
namespace['another'] = 'another test'

main.show()
app.exec_()
```
