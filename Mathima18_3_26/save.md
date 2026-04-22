'
' Created by SharpDevelop.
' User: Teacher
' Date: 22/4/2026
' Time: 12:41 μμ
' 
' To change this template use Tools | Options | Coding | Edit Standard Headers.
'
	Imports System.IO
Public Partial Class MainForm
	Private contacts As List(Of String)
	
	
	Public Sub New()
		' The Me.InitializeComponent call is required for Windows Forms designer support.
		Me.InitializeComponent()
		
		contacts = New List(Of String) From {
"Νίκος|Νίκου|67876555|nikos@in.gr",
"Anna|Ioannou|69876555|anna@in.gr",
"Γιάννης|Παπαδόπουλος|2101111111|giannis@example.com",
"Μαρία|Κωνσταντίνου|2102222222|maria@example.com",
"Πέτρος|Ιωάννου|6933333333|petros@example.com",
"Ελένη|Σταμάτη|6944444444|eleni@example.com",
"Κώστας|Δημητρίου|6955555555|kostas@example.com",
"Σοφία|Λάμπρου|6966666666|sofia@example.com",
"Δημήτρης|Αντωνίου|6977777777|dimitris@example.com",
"Κατερίνα|Γεωργίου|6988888888|katerina@example.com"
		}
	End Sub
	
	Sub Label4Click(sender As Object, e As EventArgs)
		
	End Sub
	
	Sub Button1Click(sender As Object, e As EventArgs)
		Dim firstName As String = textBox1.Text.Trim()
Dim lastName As String = textBox2.Text.Trim()
Dim phone As String = textBox3.Text.Trim()
Dim email As String =textBox4.Text.Trim()
If firstName = "" OrElse lastName = "" Then ' OrElse κάνει short cirquit. Αν
'είναι True δεν εκτιμάει την 2η συνθήκη
MessageBox.Show("First name and last name are required.")
Return
End If
' Build the big string with | delimiter
Dim line As String = firstName & "|" & lastName & "|" & phone & "|" &
email
contacts.Add(line)
MessageBox.Show("Contact added.")
textBox1.Clear()
textBox2.Clear()
textBox3.Clear()
textBox4.Clear()
textBox1.Focus()
	End Sub
	
	Sub Button2Click(sender As Object, e As EventArgs)
		textBox5.Clear()
If contacts.Count = 0 Then
textBox5.Text = "No contacts."
Return
End If
For Each line As String In contacts
' Κάνουμε split στο | και παίρνουμε τα μέρη σε array
Dim parts() As String = line.Split("|"c) ' Split στο χαρακτήρα |
'[web:37][web:43]
' Προστασία: αν δεν έχει τουλάχιστον 4 πεδία, προχώρα στην
'επόμενη γραμμή
If parts.Length < 4 Then
Continue For
End If
Dim firstName As String = parts(0)
Dim lastName As String = parts(1)
Dim phone As String = parts(2)
Dim email As String = parts(3)
textBox5.Text=textBox5.Text &firstName & " " &lastName &" "&phone &" "&email &Environment.NewLine
'Να μη βάζω το & στο τέλος του ονόματος μεταβλητής και δεν
'αναγνωρίζει το όνομα της
Next
	End Sub
	
	Sub Button3Click(sender As Object, e As EventArgs)
		Dim firstName As String = textBox1.Text.Trim()
Dim fn,ln,ph,em As String
Dim lastName As String = textBox2.Text.Trim()
Dim phone As String = textBox3.Text.Trim()
Dim email As String =textBox4.Text.Trim()
Dim found As Boolean=False
If firstName = "" OrElse lastName= "" OrElse phone="" OrElse email="" Then
MessageBox.Show("All fields are required.")
'textBox5.Clear()
Return
End If
'textBox5.Clear()
If contacts.Count = 0 Then
textBox5.Text = "No contacts."
Return
End If
For Each line As String In contacts
' Κάνουμε split στο | και παίρνουμε τα μέρη σε array
Dim parts() As String = line.Split("|"c) ' Split στο χαρακτήρα | Ο
'parts είναι μονοδιάστατος πίνακας από String και παίρνει αυτόματα το σωστό
'μέγεθος
If parts.Length < 4 Then
Continue For
End If
fn = parts(0)
ln= parts(1)
ph = parts(2)
em = parts(3)
'AndAlso κάνει short cirquit. Αν η πρώτη συνθήκη είναι ψευδής δεν
'πάει παρακάτω
If firstName = fn AndAlso lastName =
ln AndAlso phone=ph AndAlso email=em Then
found=True
Exit For' κάνει break από τη for
End If
'Να μη βάζω το & στο τέλος του ονόματος μεταβλητής και δεν
'αναγνωρίζει το όνομα της
Next
If found=True Then
MessageBox.Show("Record just found.")
textBox5.Clear()
textBox5.Text=fn & " "&ln &" "& ph &" "& em & Environment.NewLine
Else
MessageBox.Show("Record Not found.")
End If
	End Sub
	
	Sub Button4Click(sender As Object, e As EventArgs)
		
	

' Your list of strings

Dim filePath As String = "C:\Users\Teacher\Desktop\contacts.txt"

' Saves the list to the file (overwrites if it already exists)
File.WriteAllLines(filePath,contacts )

		
		
	End Sub
End Class
