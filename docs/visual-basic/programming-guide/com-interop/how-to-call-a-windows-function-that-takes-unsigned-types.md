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
ms.openlocfilehash: 78e6789e7def5deeb8394e3aefecfdc187ec6ef6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="7d1bc-102">方法: 符号なしの型を使用する Windows の機能を呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d1bc-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>
<span data-ttu-id="7d1bc-103">クラス、モジュール、または符号なし整数型のメンバーを含む構造体を使用している場合にこれらのメンバーにアクセスできます[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="7d1bc-104">符号なしの型を受け取る Windows 関数を呼び出す</span><span class="sxs-lookup"><span data-stu-id="7d1bc-104">To call a Windows function that takes an unsigned type</span></span>  
  
1.  <span data-ttu-id="7d1bc-105">使用して、 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)への通知[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]ライブラリ関数を保持する、名前がそのライブラリでは、および呼び出しシーケンスは、それを呼び出すときに、文字列を変換する方法です。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>  
  
2.  <span data-ttu-id="7d1bc-106">`Declare`ステートメントでは、使用`UInteger`、 `ULong`、 `UShort`、または`Byte`必要に応じて、各型のパラメーターを符号なしにします。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>  
  
3.  <span data-ttu-id="7d1bc-107">Windows 関数の呼び出しの名前と使用されている定数の値を検索するには、ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="7d1bc-108">これらの多くは、WinUser.h ファイルで定義されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-108">Many of these are defined in the WinUser.h file.</span></span>  
  
4.  <span data-ttu-id="7d1bc-109">コードで必要な定数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="7d1bc-110">多くの Windows 定数は、32 ビット符号なしの値、およびこれらを宣言する必要があります`As``UInteger`です。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As``UInteger`.</span></span>  
  
5.  <span data-ttu-id="7d1bc-111">通常の方法で関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-111">Call the function in the normal way.</span></span> <span data-ttu-id="7d1bc-112">次の例は、Windows の関数を呼び出して`MessageBox`、符号なし整数の引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>  
  
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
  
     <span data-ttu-id="7d1bc-113">関数をテストする`messageThroughWindows`を次のコード。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-113">You can test the function `messageThroughWindows` with the following code.</span></span>  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  <span data-ttu-id="7d1bc-114">`UInteger`、 `ULong`、 `UShort`、および`SByte`データ型がないの一部、[言語非依存および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md)(CLS)、CLS 準拠コードのコンポーネントを利用できないようにします。それらを使用します。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="7d1bc-115">Windows アプリケーション プログラミング インターフェイス (API) など、アンマネージ コードへの呼び出しを行うには、潜在的なセキュリティ リスクに対するコードを公開します。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="7d1bc-116">Windows API を呼び出すと、アンマネージ コード アクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="7d1bc-117">詳細については、次を参照してください。<xref:System.Security.Permissions.SecurityPermission>と[コード アクセス許可](http://msdn.microsoft.com/library/e5ae402f-6dda-4732-bbe8-77296630f675)です。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](http://msdn.microsoft.com/library/e5ae402f-6dda-4732-bbe8-77296630f675).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d1bc-118">参照</span><span class="sxs-lookup"><span data-stu-id="7d1bc-118">See Also</span></span>  
 [<span data-ttu-id="7d1bc-119">データの種類</span><span class="sxs-lookup"><span data-stu-id="7d1bc-119">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="7d1bc-120">整数データ型</span><span class="sxs-lookup"><span data-stu-id="7d1bc-120">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="7d1bc-121">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="7d1bc-121">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
 [<span data-ttu-id="7d1bc-122">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="7d1bc-122">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="7d1bc-123">チュートリアル : Windows API の呼び出し</span><span class="sxs-lookup"><span data-stu-id="7d1bc-123">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
