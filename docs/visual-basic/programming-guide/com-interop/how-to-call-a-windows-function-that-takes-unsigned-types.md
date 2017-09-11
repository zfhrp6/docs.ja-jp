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
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7b6b1d46b6ccab0ec8d63fb8b7d8722b518b81b4
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="58bff-102">方法: 符号なしの型を使用する Windows の機能を呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58bff-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>
<span data-ttu-id="58bff-103">クラス、モジュール、または符号なし整数型のメンバーを含む構造体を使用している場合は、これらのメンバーとをアクセスすることができます[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="58bff-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="58bff-104">符号なしの型を受け取る Windows 関数を呼び出す</span><span class="sxs-lookup"><span data-stu-id="58bff-104">To call a Windows function that takes an unsigned type</span></span>  
  
1.  <span data-ttu-id="58bff-105">使用して、[宣言ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)のに[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]関数を保持するためのライブラリ、その名前がそのライブラリには、および呼び出しシーケンスは、それを呼び出すときに文字列を変換する方法です。</span><span class="sxs-lookup"><span data-stu-id="58bff-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>  
  
2.  <span data-ttu-id="58bff-106">`Declare`ステートメントを使用して`UInteger`、 `ULong`、 `UShort`、または`Byte`必要に応じて、符号なしの型の各パラメーターにします。</span><span class="sxs-lookup"><span data-stu-id="58bff-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>  
  
3.  <span data-ttu-id="58bff-107">Windows 関数の名前と使用されている定数の値を検索する呼び出しと、ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="58bff-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="58bff-108">これらの多くは、WinUser.h ファイルで定義されます。</span><span class="sxs-lookup"><span data-stu-id="58bff-108">Many of these are defined in the WinUser.h file.</span></span>  
  
4.  <span data-ttu-id="58bff-109">コードで必要な定数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="58bff-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="58bff-110">多くの Windows 定数は、32 ビット符号なしの値と、これらを宣言する必要があります`As``UInteger`します。</span><span class="sxs-lookup"><span data-stu-id="58bff-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As``UInteger`.</span></span>  
  
5.  <span data-ttu-id="58bff-111">通常の方法で、関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="58bff-111">Call the function in the normal way.</span></span> <span data-ttu-id="58bff-112">次の例は、Windows の関数を呼び出して`MessageBox`、符号なし整数の引数を受け取る。</span><span class="sxs-lookup"><span data-stu-id="58bff-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>  
  
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
  
     <span data-ttu-id="58bff-113">この関数をテストする`messageThroughWindows`を次のコードです。</span><span class="sxs-lookup"><span data-stu-id="58bff-113">You can test the function `messageThroughWindows` with the following code.</span></span>  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  <span data-ttu-id="58bff-114">`UInteger`、 `ULong`、 `UShort`、および`SByte`データ型がないの一部では、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS) には、CLS 準拠のコードは、それらを使用するコンポーネントを使用できないようにします。</span><span class="sxs-lookup"><span data-stu-id="58bff-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="58bff-115">Windows アプリケーション プログラミング インターフェイス (API) など、アンマネージ コードへの呼び出しを行うには、潜在的なセキュリティ リスクにコードを公開します。</span><span class="sxs-lookup"><span data-stu-id="58bff-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="58bff-116">Windows API を呼び出すと、アンマネージ コード アクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="58bff-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="58bff-117">詳細については、次を参照してください<xref:System.Security.Permissions.SecurityPermission>と[コード アクセス許可](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675)。</xref:System.Security.Permissions.SecurityPermission> 。</span><span class="sxs-lookup"><span data-stu-id="58bff-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58bff-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="58bff-118">See Also</span></span>  
 <span data-ttu-id="58bff-119">[データ型](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="58bff-119">[Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="58bff-120"> [整数データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="58bff-120"> [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span></span>  
<span data-ttu-id="58bff-121"> [Uinteger 型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="58bff-121"> [UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) </span></span>  
<span data-ttu-id="58bff-122"> [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="58bff-122"> [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) </span></span>  
<span data-ttu-id="58bff-123"> [チュートリアル : Windows API の呼び出し](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)</span><span class="sxs-lookup"><span data-stu-id="58bff-123"> [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)</span></span>
