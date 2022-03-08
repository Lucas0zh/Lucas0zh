import chess

'''
board = chess.Board()
print(board)
board.push_san("e4")
print(board)
board.push(chess.Move.from_uci("e4e5"))
print(board)
board.push(chess.Move.from_uci("e5e6"))
print(board)
board.push(chess.Move.from_uci("e1e2"))
print(board)
print(board.board_fen())

board.push(chess.Move.from_uci("f3f7"))
print(board)
print(board.board_fen())'''

import chess.svg
board = chess.Board("8/8/8/8/4N3/8/8/8 w - - 0 1")
squares = board.attacks(chess.E4)
chess.svg.board(board, squares=squares, size=350)
print(board)
