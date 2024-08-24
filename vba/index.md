---
title: VBA Macros
layout: home
typora-copy-images-to: ./images
typora-root-url: ./../
---
### PowerPoint Slide Note Ripper

Overwrite the Notes field on every slide with the video object name of the current slide and the video object name of the next slide.

Used for Linebreakers shows so I can see which songs are up now and next on the PPT notes.

```vba
Sub UpdateSlideNotes()

Dim oPres As Presentation
Dim oSlides As Slides
Dim oSlide As Slide
Dim oShapes As Shapes
Dim oSh As Shape
Dim NotesText As String
Dim FileNum As Integer
Dim PathSep As String

#If Mac Then
    PathSep = ":"
#Else
    PathSep = "\"
#End If

Set oPres = ActivePresentation
Set oSlides = oPres.Slides

Dim ThisName As String
Dim ThisSlide As Slide
Dim LastName As String
Dim LastSlide As Slide

For Each oSlide In oSlides
    ThisName = ""
    For Each oShape In oSlide.Shapes
        If oShape.Type = msoMedia Then
            If oShape.MediaType = ppMediaTypeMovie Then
                ThisName = oShape.Name
            End If
        End If
    Next
    oSlide.NotesPage.Shapes(2).TextFrame.TextRange.Text = "THIS: " & ThisName
    If Not LastSlide Is Nothing Then
        Set Notes = LastSlide.NotesPage.Shapes(2).TextFrame.TextRange
        Notes.Text = Notes.Text & vbNewLine & vbNewLine & "NEXT: " & ThisName
    End If
    If (ThisName <> "") Then
        Set LastSlide = oSlide
    End If
Next oSlide

End Sub

```