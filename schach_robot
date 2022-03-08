import kivy
import chess
kivy.require('1.9.0') # Mindest-Version von Kivy
from in_game_gui import Field
from fen2pil import draw
from kivy.app import App
from kivy.uix.button import Button
from kivy.uix.widget import Widget
from kivy.core.window import Window
from kivy.uix.dropdown import DropDown
from kivy.uix.image import Image, AsyncImage

x = 400
y = 800

class Button_Widget(Widget):
    
    def __init__(self, **kwargs):
        
        super(Button_Widget, self).__init__(**kwargs)
        '''
        btn1 = Button(text="Singleplayer", height=50, width=300, pos=(50,250))
        btn1.bind(on_press = drop_down.open)
        self.add_widget(btn1)'''
        
        btn2 = Button(text="Multiplayer", height=50, width=200, pos=(100,375))
        btn2.bind(on_press = self.callback)
        self.add_widget(btn2)
        
        btn3 = Button(text="Options", height=50, width=200, pos=(100,275))
        btn3.bind(on_press = self.callback)
        self.add_widget(btn3)
        
        
        
        drop_down = DropDown()
        drop_btn1 = Button(text="Create score", size_hint_y=None, height=20)
        drop_btn1.bind(on_press = self.newWindow)
        drop_down.add_widget(drop_btn1)
        drop_btn2 = Button(text="Load score", size_hint_y=None, height=20)
        drop_down.add_widget(drop_btn2)
        
        btn1 = Button(text="Singleplayer", height=50, width=200, pos=(100,475))
        btn1.bind(on_press = drop_down.open)
        self.add_widget(btn1)
        
        drop_down.bind(on_select = lambda instance, x: setattr(main_button, 'text', x))
        
    
    def callback(self, instance):
        print("Button is pressed")
        print('The button % s state is <%s>' % (instance, instance.state))
        
    def newWindow(self, instance):
        self.clear_widgets()
        btn4 = Button(background_normal="pfeil.png", height=20, width=40, pos=(0,780), background_color="grey")
        btn4.bind(on_press = self.back)
        self.add_widget(btn4)
        
        fen = chess.STARTING_BOARD_FEN
        board = chess.Board()
        board.set_fen(fen)
        print(board.legal_moves.count())
        

        self.create_chess_img(fen)
        
        field = Field(x,(0,int(x/2)),self, fen)
        
    def create_chess_img(self, fen):
        pil_image = draw.transform_fen_pil(
            fen=fen,
            board_size=480,
            light_color=(255, 253, 208),
            dark_color=(181, 135, 99)
        )
        pil_image.save('test.png')
        img = Image(source='test.png', height=x, width=x, pos=(0,x/2))
        self.add_widget(img)
        
    def back(self, instance):
        self.clear_widgets()
        self.__init__()
        

class Chess(App):

    def build(self):
        Window.size = (x,y)
        return Button_Widget()
        
if __name__== "__main__":
    Chess().run()
