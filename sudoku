import java.io.IOException;

public class SudokuSolver {
    
    public int [][]board;
    public int length;
    
    public SudokuSolver() {
        board = new int[][] {
                {3, 0, 6, 5, 0, 8, 4, 0, 0},
                {5, 2, 0, 0, 0, 0, 0, 0, 0},
                {0, 8, 7, 0, 0, 0, 0, 3, 1},
                {0, 0, 3, 0, 1, 0, 0, 8, 0},
                {9, 0, 0, 8, 6, 3, 0, 0, 5},
                {0, 5, 0, 0, 9, 0, 6, 0, 0},
                {1, 3, 0, 0, 0, 0, 2, 5, 0},
                {0, 0, 0, 0, 0, 0, 0, 7, 4},
                {0, 0, 5, 2, 0, 6, 3, 0, 0}
        };
        
        length = board.length;
    }
    
    public boolean solve() {
        int row = 0;
        int col = 0;
        boolean isFilled = true;

        for(row=0; row<length; row++) {
            for(col=0; col<length; col++) {
                if(board[row][col] == 0) {
                    isFilled = false;
                    break;
                }
            }
            if(!isFilled)
                break;
        }

        if(isFilled)
            return true;

        for(int num=1; num<=length; num++) {
            if(isSafe(num, row, col)) {
                board[row][col] = num;
                if (solve())
                    return true;
                else
                    board[row][col] = 0;
            }
        }
        return false;
    }


    public boolean isSafe (int no, int row, int col) {
        if(rowSafe(row, no) && colSafe(col, no) && boxSafe(board, row, col, no))
            return true;
        return false;
    }


    public boolean rowSafe (int startRow, int assingedNumber) {
        for(int i=0; i<9; i++) {
            if(board[startRow][i] == assingedNumber)
                return false;
        }
        return true;
    }

    public boolean colSafe (int startCol, int assingedNumber) {
        for(int i=0; i<9; i++) {
            if(board[i][startCol] == assingedNumber)
                return false;
        }
        return true;
    }


    public boolean boxSafe(int [][]board, int row, int col, int assingedNumber) {
        int startRow = row - (row%3);
        int startCol = col - (col%3);

        for(int i=startRow; i<startRow+3; i++) {
            for(int j=startCol; j<startCol+3; j++) {
                if(board[i][j] == assingedNumber)
                    return false;
            }
        }
        return true;
    }


    public void printBoard() {
        for(int i=0;i<=length;i++) {
            if(i==length){
                System.out.println("- - - - - - - - - - - - -");
                break;
            }
            else if(i==0 || i%3==0)
                System.out.println("- - - - - - - - - - - - -");

            for(int j=0;j<length;j++) {
                if(j==0 || j%3==0)
                    System.out.print("| ");
                if(board[i][j]==0)
                    System.out.print(". ");
                else
                    System.out.print(board[i][j] + " ");
            }
            System.out.print("|");
            System.out.println();
        }
    }

    public static void main(String[] args) {
        try {
            SudokuSolver sudoku = new SudokuSolver();
            sudoku.printBoard();

            System.out.println("Enter any key to solve...");
            char enterKey = (char) System.in.read();

            if (sudoku.solve()) {
                sudoku.printBoard();
            }
        }
        catch(IOException ae) {
            System.out.println("Error: " + ae.getMessage());
        }

    }
}
