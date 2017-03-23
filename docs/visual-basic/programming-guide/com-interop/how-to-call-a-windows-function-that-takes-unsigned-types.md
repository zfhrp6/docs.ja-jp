---
title: "方法: 符号なしの型 (Visual Basic の場合)、Windows 関数を呼び出す |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Windows functions, calling
- unsigned data types
- UShort data type, using
- functions [Visual Basic], calling Windows functions
- ULong data type, using
- UInteger data type, using
- data types [Visual Basic], using
- unsigned types
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types, using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fbff07f4923b0633a2bc9b4fd558d9d51f64370a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>方法: 符号なしの型を使用する Windows の機能を呼び出す (Visual Basic)
クラス、モジュール、または符号なし整数型のメンバーを含む構造体を使用している場合は、これらのメンバーとをアクセスすることができます[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>符号なしの型を受け取る Windows 関数を呼び出す  
  
1.  使用して、[宣言ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)のに[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]関数を保持するためのライブラリ、その名前がそのライブラリには、および呼び出しシーケンスは、それを呼び出すときに文字列を変換する方法です。  
  
2.  `Declare`ステートメントを使用して`UInteger`、 `ULong`、 `UShort`、または`Byte`必要に応じて、符号なしの型の各パラメーターにします。  
  
3.  Windows 関数の名前と使用されている定数の値を検索する呼び出しと、ドキュメントを参照してください。 これらの多くは、WinUser.h ファイルで定義されます。  
  
4.  コードで必要な定数を宣言します。 多くの Windows 定数は、32 ビット符号なしの値と、これらを宣言する必要があります`As``UInteger`します。  
  
5.  通常の方法で、関数を呼び出します。 次の例は、Windows の関数を呼び出して`MessageBox`、符号なし整数の引数を受け取る。  
  
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
  
     この関数をテストする`messageThroughWindows`を次のコードです。  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  `UInteger`、 `ULong`、 `UShort`、および`SByte`データ型がないの一部では、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS) には、CLS 準拠のコードは、それらを使用するコンポーネントを使用できないようにします。  
  
    > [!IMPORTANT]
    >  Windows アプリケーション プログラミング インターフェイス (API) など、アンマネージ コードへの呼び出しを行うには、潜在的なセキュリティ リスクにコードを公開します。  
  
    > [!IMPORTANT]
    >  Windows API を呼び出すと、アンマネージ コード アクセス許可が必要です。 詳細については、次を参照してください<xref:System.Security.Permissions.SecurityPermission>と[コード アクセス許可](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675)。</xref:System.Security.Permissions.SecurityPermission> 。  
  
## <a name="see-also"></a>関連項目  
 [データ型](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [整数データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Uinteger 型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)   
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [チュートリアル : Windows API の呼び出し](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
