---
title: "How to: Dispose of a System Resource (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Using statement, disposing of system resources"
  - "Visual Basic code, control flow"
  - "system resources, disposing of"
  - "resources [Visual Basic], disposing of system"
  - "system resources"
  - "Using statement, Using...End Using"
  - "Using block"
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Dispose of a System Resource (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Using` ブロックを使用して、コードがブロックを終了するときに、必ずシステムでリソースが破棄されるようにできます。  これは、大量のメモリを消費するシステム リソースを使用している場合、または他のコンポーネントでもシステム リソースを使用できるようにする場合に便利です。  
  
### コードがデータベース処理を終了するときにデータベース接続を切断するには  
  
1.  ソース ファイルの先頭に、データベース接続用の適切な [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) が含まれていることを確認します \(この場合は、<xref:System.Data.SqlClient>\)。  
  
2.  `Using` および `End Using` ステートメントを使用して、`Using` ブロックを作成します。  ブロック内部には、データベース接続を処理するコードを含めます。  
  
3.  接続を宣言し、`Using` ステートメントの一部として、インスタンスを作成します。  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     システムは、未処理の例外も含めて、どのような場合であってもブロックを終了するときに、リソースを破棄します。  
  
     `sqc` の範囲はブロックに限定されているため、`Using` ブロックの外側からはこれにアクセスできないことに注意してください。  
  
     ファイル処理または COM ラッパーなどのシステム リソースに対しても、これと同じ技法を使用できます。  `Using` ブロックを終了した後、他のコンポーネントでそのリソースを確実に使用できるようにするには、`Using` ブロックを使用します。  
  
## 参照  
 <xref:System.Data.SqlClient.SqlConnection>   
 [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)   
 [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md)