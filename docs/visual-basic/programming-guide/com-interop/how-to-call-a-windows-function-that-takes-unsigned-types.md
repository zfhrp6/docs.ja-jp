---
title: "方法: 符号なしの型を使用する Windows の機能を呼び出す (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Windows functions [Visual Basic], calling
- unsigned data types [Visual Basic]
- UShort data type [Visual Basic], using
- functions [Visual Basic], calling Windows functions
- ULong data type [Visual Basic], using
- UInteger data type [Visual Basic], using
- data types [Visual Basic], using
- unsigned types [Visual Basic]
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types [Visual Basic], using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3663ca5d3e0e2c94530d4a19ebff0022f495f3d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>方法: 符号なしの型を使用する Windows の機能を呼び出す (Visual Basic)
クラス、モジュール、または符号なし整数型のメンバーを含む構造体を使用している場合にこれらのメンバーにアクセスできます[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]です。  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>符号なしの型を受け取る Windows 関数を呼び出す  
  
1.  使用して、 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)への通知[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]ライブラリ関数を保持する、名前がそのライブラリでは、および呼び出しシーケンスは、それを呼び出すときに、文字列を変換する方法です。  
  
2.  `Declare`ステートメントでは、使用`UInteger`、 `ULong`、 `UShort`、または`Byte`必要に応じて、各型のパラメーターを符号なしにします。  
  
3.  Windows 関数の呼び出しの名前と使用されている定数の値を検索するには、ドキュメントを参照してください。 これらの多くは、WinUser.h ファイルで定義されます。  
  
4.  コードで必要な定数を宣言します。 多くの Windows 定数は、32 ビット符号なしの値、およびこれらを宣言する必要があります`As``UInteger`です。  
  
5.  通常の方法で関数を呼び出します。 次の例は、Windows の関数を呼び出して`MessageBox`、符号なし整数の引数を受け取ります。  
  
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
  
     関数をテストする`messageThroughWindows`を次のコード。  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  `UInteger`、 `ULong`、 `UShort`、および`SByte`データ型がないの一部、[言語非依存および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md)(CLS)、CLS 準拠コードのコンポーネントを利用できないようにします。それらを使用します。  
  
    > [!IMPORTANT]
    >  Windows アプリケーション プログラミング インターフェイス (API) など、アンマネージ コードへの呼び出しを行うには、潜在的なセキュリティ リスクに対するコードを公開します。  
  
    > [!IMPORTANT]
    >  Windows API を呼び出すと、アンマネージ コード アクセス許可が必要です。 詳細については、次を参照してください。<xref:System.Security.Permissions.SecurityPermission>と[コード アクセス許可](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675)です。  
  
## <a name="see-also"></a>参照  
 [データの種類](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [整数データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [UInteger データ型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [チュートリアル : Windows API の呼び出し](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
