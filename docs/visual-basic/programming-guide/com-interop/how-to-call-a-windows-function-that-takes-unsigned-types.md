---
title: "How to: Call a Windows Function that Takes Unsigned Types (Visual Basic) | Microsoft Docs"
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
  - "Windows functions, calling"
  - "unsigned data types"
  - "UShort data type, using"
  - "functions [Visual Basic], calling Windows functions"
  - "ULong data type, using"
  - "UInteger data type, using"
  - "data types [Visual Basic], using"
  - "unsigned types"
  - "data types [Visual Basic], unsigned"
  - "data types [Visual Basic], numeric"
  - "unsigned types, using"
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

符号なし整数型のメンバーがあるクラス、モジュール、または構造体を使用している場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] を使用してこれらのメンバーにアクセスできます。  
  
### 符号なしの型を使用する Windows の機能を呼び出すには  
  
1.  [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)を使用して、機能を保持しているライブラリ、ライブラリ内での名前、呼び出し元のシーケンス、呼び出し時に文字列を変換する方法を [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] に伝えます。  
  
2.  `Declare` ステートメントで、符号なしの型を持つ各パラメーターに応じて `UInteger`、`ULong`、`UShort`、または `Byte` を使用します。  
  
3.  呼び出している Windows の機能のドキュメントを参照し、使用されている定数の名前および値を調べます。  これらの多くは、WinUser.h ファイルで定義されています。  
  
4.  コードで、必要な定数を宣言します。  多くの Windows 定数は 32 ビットの符号なしの値であり、これらの `As` `UInteger` を宣言する必要があります。  
  
5.  通常の方法で機能を呼び出します。  符号なしの整数の引数を使用する、Windows の機能である `MessageBox` を呼び出す例を次に示します。  
  
    ```  
    Public Class windowsMessage  
        Private Declare Auto Function mb Lib "user32.dll" Alias "MessageBox" (  
            ByVal hWnd As Integer,   
            ByVal lpText As String,   
            ByVal lpCaption As String,   
            ByVal uType As UInteger) As Integer  
        Private Const MB_OK As UInteger = 0  
        Private Const MB_ICONEXCLAMATION As UInteger = &H30  
        Private Const IDOK As UInteger = 1  
        Private Const IDCLOSE As UInteger = 8  
        Private Const c As UInteger = MB_OK Or MB_ICONEXCLAMATION  
        Public Function messageThroughWindows() As String  
            Dim r As Integer = mb(0, "Click OK if you see this!",   
                "Windows API call", c)  
            Dim s As String = "Windows API MessageBox returned " &  
                 CStr(r)& vbCrLf & "(IDOK = " & CStr(IDOK) &  
                 ", IDCLOSE = " & CStr(IDCLOSE) & ")"  
            Return s  
        End Function  
    End Class  
    ```  
  
     `messageThroughWindows` の機能をテストするためには、次のコードを使用してください。  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  `UInteger`、`ULong`、`UShort`、および `SByte` データ型は、[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 一部ではありません。したがって、CLS 準拠のコードでは、これらを使用するコンポーネントを使用できません。  
  
    > [!IMPORTANT]
    >  Windows アプリケーション プログラミング インターフェイス \(API: Application Programming Interface\) などのアンマネージ コードへの呼び出しを実行すると、潜在的なセキュリティ リスクにコードが公開されます。  
  
    > [!IMPORTANT]
    >  Windows API の呼び出しにはアンマネージ コード アクセス許可が必要です。ただし、部分的に信頼されている状況でこの許可を使用すると、プログラムの実行に影響を及ぼす場合があります。  詳細については、「<xref:System.Security.Permissions.SecurityPermission>」および「[Code Access Permissions](http://msdn.microsoft.com/ja-jp/e5ae402f-6dda-4732-bbe8-77296630f675)」を参照してください。  
  
## 参照  
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)   
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)