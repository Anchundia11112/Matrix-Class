import math
from math import sqrt
import numbers

def zeroes(height, width):
        """
        Creates a matrix of zeroes.
        """
        g = [[0.0 for _ in range(width)] for __ in range(height)]
        return Matrix(g)

def identity(n):
        """
        Creates a n x n identity matrix.
        """
        I = zeroes(n, n)
        for i in range(n):
            I.g[i][i] = 1.0
        return I

class Matrix(object):

    # Constructor
    def __init__(self, grid):
        self.g = grid
        self.h = len(grid)
        self.w = len(grid[0])

    #
    # Primary matrix math methods
    #############################
 
    def determinant(self):
        """
        Calculates the determinant of a 1x1 or 2x2 matrix.
        """
        if not self.is_square():
            raise(ValueError, "Cannot calculate determinant of non-square matrix.")
        if self.h > 2:
            raise(NotImplementedError, "Calculating determinant not implemented for matrices largerer than 2x2.")
        
        # TODO - your code here 
        
        if(self.h == 1 and self.w == 1):
            return self
        else:
            equal_index_list = []
            unequal_index_list = []
            determinant_result = 0
        
            for indexR, row_values in enumerate(self.g):    #Both can be slef.g since we need a square matrix
                new_row = []
                for indexC, column_values in enumerate(self.g):
                    if(row_values == column_values):
                        equal_index_list.insert(indexR,self[indexR][indexC])
                    else:
                        unequal_index_list.insert(indexR,self[indexR][indexC])
            determinant_result = (equal_index_list[0] * equal_index_list[1]) - (unequal_index_list[0] * unequal_index_list[1])
            return determinant_result 

    def trace(self):
        """
        Calculates the trace of a matrix (sum of diagonal entries).
        """
        if not self.is_square():
            raise(ValueError, "Cannot calculate the trace of a non-square matrix.")
            
                    
        important_list = []    
        for indexR, row_values in enumerate(self.g):    #Both can be slef.g since we need a square matrix
            new_row = []
            for indexC, column_values in enumerate(self.g):
                if(row_values == column_values):
                    important_list.insert(indexR,self[indexR][indexC])
                else:
                    continue
        di_sum = sum(important_list)
        return di_sum

        # TODO - your code here

    def inverse(self):
        """
        Calculates the inverse of a 1x1 or 2x2 Matrix.
        """
        determinant_of_matrix = self.determinant()
        if not self.is_square():
            raise(ValueError, "Non-square Matrix does not have an inverse.")
        if self.h > 2:
            raise(NotImplementedError, "inversion not implemented for matrices larger than 2x2.")
        
         # TODO - your code here
            
        myList = []
        number = 1
        
        if(self.h == 1 and self.w == 1):
            for indexR, row_values in enumerate(self.g): #Both can be slef.g since we need a square matrix
                for indexC, column_values in enumerate(self.g):
                    myList = 1/self[indexR][indexC]
            return Matrix[myList]
        else:
            return Matrix([[self[1][1]/determinant_of_matrix, -1*self[0][1]/determinant_of_matrix],
                [-1*self[1][0]/determinant_of_matrix, self[0][0]/determinant_of_matrix]])
            
    def T(self):
        """
        Returns a transposed copy of this Matrix.
        """
        # TODO - your code here
        matrix_transpose = [list(i) for i in zip(*self)] 
        return Matrix(matrix_transpose)

    def is_square(self):
        return self.h == self.w

    #
    # Begin Operator Overloading
    ############################
    def __getitem__(self,idx):
        """
        Defines the behavior of using square brackets [] on instances
        of this class.

        Example:

        > my_matrix = Matrix([ [1, 2], [3, 4] ])
        > my_matrix[0]
          [1, 2]

        > my_matrix[0][0]
          1
        """
        return self.g[idx]

    def __repr__(self):
        """
        Defines the behavior of calling print on an instance of this class.
        """
        s = ""
        for row in self.g:
            s += " ".join(["{} ".format(x) for x in row])
            s += "\n"
        return s

    def __add__(self,other):
        """
        Defines the behavior of the + operator
        """
        if self.h != other.h or self.w != other.w:
            raise(ValueError, "Matrices can only be added if the dimensions are the same") 
        #   
        # TODO - your code here
        #
        
        
        emptyMatrix = []
        for indexR, row_values in enumerate(self.g): 
            new_row = []
            for indexC, column_values in enumerate(self.g):
                added_row = self.g[indexR][indexC] + other.g[indexR][indexC]
                new_row.append(added_row)
            emptyMatrix.append(new_row)
      
        return Matrix(emptyMatrix)  
        
        
        
    def __neg__(self):
        """
        Defines the behavior of - operator (NOT subtraction)

        Example:

        > my_matrix = Matrix([ [1, 2], [3, 4] ])
        > negative  = -my_matrix
        > print(negative)
          -1.0  -2.0
          -3.0  -4.0
        """
        #   
        # TODO - your code here
        #
        emptyMatrix = []
        for indexR, row_values in enumerate(self.g):
            new_row = []
            for indexC, column_values in enumerate(self.g):
                the_new = self[indexR][indexC] * -1
                new_row.append(the_new)
            emptyMatrix.append(new_row)
            new_row = []
        return Matrix(emptyMatrix)

    def __sub__(self, other):
        """
        Defines the behavior of - operator (as subtraction)
        """
        #   
        # TODO - your code here
        #
        
        emptyMatrix = []
        for indexR, row_values in enumerate(self.g): 
            new_row = []
            for indexC, column_values in enumerate(self.g):
                added_row = self[indexR][indexC] - other[indexR][indexC]
                new_row.append(added_row)
            emptyMatrix.append(new_row)
            new_row = []
       
        return Matrix(emptyMatrix)
        
        
    def __mul__(self, other):
        """
        Defines the behavior of * operator (matrix multiplication)
        """
        #   
        # TODO - your code here
        #
        
        def dot_product(vector1, vector2):
            result = 0
            for i in range(len(vector1)):
                value_1 = vector1[i]
                value_2 = vector2[i]
                result += value_1 * value_2
            return result
    
        transpose_matrixB = other.T()
        matrix_b_size = other.w
        emptyMatrix = []
        '''
        for indexR, row_values in enumerate(self.g): 
            new_row = []
            for indexC, other_row_values in enumerate(transpose_matrixB):
                added_row = dot_product(self.g[row_values], transpose_matrixB[other_row_values])
                new_row.append(added_row)
            emptyMatrix.append(new_row)
        return Matrix(emptyMatrix)
        '''
        for row_values in range(self.h):
            new_row = []
            for other_row_values in range(transpose_matrixB.h):
                dotted_row = dot_product(self.g[row_values],transpose_matrixB[other_row_values])
                new_row.append(dotted_row)
            emptyMatrix.append(new_row)
        return Matrix(emptyMatrix)
    def __rmul__(self, other):
        """
        Called when the thing on the left of the * is not a matrix.

        Example:

        > identity = Matrix([ [1,0], [0,1] ])
        > doubled  = 2 * identity
        > print(doubled)
          2.0  0.0
          0.0  2.0
        """
            
            
        if isinstance(other, numbers.Number):
            pass
            #   
            # TODO - your code here
            #
            
            r = []
            for i in range(self.h):
                row = self[i]
                new_row = [] # empty row for now
                for j in range(self.h):
                    m_ij = self[i][j]
                    r_ij = other * m_ij
                    new_row.append(r_ij)
                r.append(new_row)
            return Matrix(r)

            
