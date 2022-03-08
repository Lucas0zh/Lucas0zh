import kivy
import chess

from fen2pil import draw
from kivy.app import App
from kivy.uix.button import Button
from kivy.uix.widget import Widget


class Field(Widget):
    
    def __init__(self, width, pos, window, fen):
        
        #super(Field, self).__init__(**kwargs)
        size = width/8
        posX = pos[0]
        posY = pos[1]
        self.fen = fen
        self.button_list = []
        
        for i in range(64):
            print("("+str(posX)+","+str(posY)+")")
            btn = Button(height = size, width=size, pos=(posX, posY),background_color=(0,0,0,0))#, rgba=(1,0,0,1))
            btn.bind(on_press=self.callback)
            self.button_list.append(btn)
            window.add_widget(btn)
            posX+=size
            if (i+1)%8 == 0:
                posY+=size
                posX-=size*8
                
        print(self.button_list)    
                
    def callback(self, instance):
        print("test")
        
        for button in self.button_list:
            button.background_color = (0,0,0,0)
        
        instance.background_color=(1,0,0,1)
        self.temp = instance
        board = chess.Board()
        board.set_fen(self.fen)
        current_pos = self.indexToField(instance)
        
        legal_moves = board.legal_moves
        legal_moves_string = []
        for move in legal_moves:
            legal_moves_string.append(str(move))
        
        print(legal_moves_string)
        
        for i in legal_moves_string:
            if current_pos[0] == i[0] and current_pos[1] == i[1]:
                print(i)
                temp_string = i[2]+i[3]
                print(self.fieldToIndex(temp_string))
                self.button_list[self.fieldToIndex(temp_string)].background_color = "green"
        
        
        
        
        
        
    def indexToField(self, instance):
        index = self.button_list.index(instance)
        nr = int((index)/8)+1
        strL = ""
        strN = (index)%8      
        
        if strN == 0:
            strL = "a"
        elif strN == 1:
            strL = "b"
        elif strN == 2:
            strL = "c"
        elif strN == 3:
            strL = "d"
        elif strN == 4:
            strL = "e"
        elif strN == 5:
            strL = "f"
        elif strN == 6:
            strL = "g"
        elif strN == 7:
            strL = "h"
            
        return strL+str(nr)
    
    def fieldToIndex(self,field):
        letter = field[0]
        nr = int(field[1])
        index  = 0
        
        if letter =="b":
            index +=1
        elif letter =="c":
            index +=2
        elif letter =="d":
            index +=3
        elif letter =="e":
            index +=4
        elif letter =="f":
            index +=5
        elif letter =="g":
            index +=6
        elif letter =="h":
            index +=7
        
        index += (nr-1)*8
        
        return int(index)
