
Imports System.Data.SqlClient
Public Class Form1

    Friend Class Sqlconnection
        Private connectionString As String
        Public Sub New(connectionString As String)
            Me.connectionString = connectionString
        End Sub
    End Class


    Private Class Sqlcommand
        Private SqlQuery As String
        Private connection As Sqlconnection

        Public Sub New(SqlQuery As String, connection As Sqlconnection)
            Me.SqlQuery = SqlQuery
            Me.connection = connection
        End Sub
    End Class

    Dim connectionString As String = "Data Source=DESKTOP-98AV7CI;Initial Catalog=LibraryDB;Integrated Security=True"
    Dim connection As New Sqlconnection(connectionString)

    Private Sub LoadData()

        Try

            Dim sqlQuery As String = "SELECT * Tables"
            Dim command As New Sqlcommand(sqlQuery, connection)




        Catch ex As Exception
            MessageBox.Show("Error loading data: " & ex.Message)
        Finally

        End Try
    End Sub



    Private Sub btnAdd_Click(sender As Object, e As EventArgs) Handles btnAdd.Click
        Try
            Dim query As String = "INSERT INTO Books (Title, Author, YearPublished, Genre) VALUES (@Title, @Author, @YearPublished, @Genre)"

        Catch ex As Exception
            MessageBox.Show("Error adding data: " & ex.Message, "Error", MessageBoxButtons.OK, MessageBoxIcon.Error)
        End Try
    End Sub

    Private Sub btnUpdate_Click(sender As Object, e As EventArgs) Handles btnUpdate.Click
        Try
            Dim query As String = "UPDATE Books SET Title=@Title, Author=@Author, YearPublished=@YearPublished, Genre=@Genre WHERE ID=@ID"

        Catch ex As Exception
            MessageBox.Show("Error updating data: " & ex.Message, "Error", MessageBoxButtons.OK, MessageBoxIcon.Error)
        End Try
    End Sub



    Private Sub btnDelete_Click(sender As Object, e As EventArgs) Handles btnDelete.Click
        Try
            Dim query As String = "DELETE FROM Books WHERE ID=@ID"

        Catch ex As Exception
            MessageBox.Show("Error deleting data: " & ex.Message, "Error", MessageBoxButtons.OK, MessageBoxIcon.Error)
        End Try
    End Sub

    Private Sub btnClear_Click(sender As Object, e As EventArgs) Handles btnClear.Click
        txtTitle.Clear()
        txtAuthor.Clear()
        txtYearPublished.Clear()
        txtGenre.Clear()
    End Sub

    Private Sub LibraryManagementSystem_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        LoadData()
    End Sub

    Private Sub Label2_Click(sender As Object, e As EventArgs) Handles Label2.Click

    End Sub
End Class
