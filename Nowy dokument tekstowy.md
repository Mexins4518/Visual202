Imports System.Net
Public Class Form1

    Private Const Fortnite As String = "https://pastebin.com/raw/faVa9Wax"
    Private Const Minecraft As String = "https://pastebin.com/raw/9WJNA4Rf"
    Private wc As WebClient
    Private R As Random

    Sub New()


        InitializeComponent()

        wc = New WebClient
        R = New Random


    End Sub

    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load
        txtUser.ReadOnly = True
        txtPassword.ReadOnly = True
    End Sub

    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
        GenerateAccount()
    End Sub

    Sub GenerateAccount()
        Select Case comboType.SelectedItem
            Case "Randomize Fortnite Account"
                Dim Account As String() = wc.DownloadString(Fortnite).Split(Environment.NewLine)
                ParseAccount(Account(R.Next(1, Account.Length)))
            Case Else
                MsgBox("Select the type of account to generate", MsgBoxStyle.Exclamation)
        End Select
    End Sub

    Private Sub ParseAccount(ByVal Account As String)
        txtUser.Text = Account.Split(":")(0)
        txtPassword.Text = Account.Split(":")(1)
    End Sub

    Private Function Account() As Object
        Throw New NotImplementedException
    End Function

End Class