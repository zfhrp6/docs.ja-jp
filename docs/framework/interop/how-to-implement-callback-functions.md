---
title: "方法: コールバック関数を実装する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords: callback function, implementing
ms.assetid: e55b3712-b9ea-4453-bd9a-ad5cfa2f6bfa
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 819861f9bf13f9af3fab7a1ea7ffc697c1d98926
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-callback-functions"></a><span data-ttu-id="cbc80-102">方法: コールバック関数を実装する</span><span class="sxs-lookup"><span data-stu-id="cbc80-102">How to: Implement Callback Functions</span></span>
<span data-ttu-id="cbc80-103">次の手順と例は、マネージ アプリケーションがプラットフォーム呼び出しを使用して、ローカル コンピューター上の各ウィンドウのハンドル値を出力する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="cbc80-103">The following procedure and example demonstrate how a managed application, using platform invoke, can print the handle value for each window on the local computer.</span></span> <span data-ttu-id="cbc80-104">具体的には、この手順と例では **EnumWindows** 関数を使用してウィンドウのリストをステップスルーし、(CallBack という名前の) マネージ コールバック関数を使用してウィンドウ ハンドルの値を出力します。</span><span class="sxs-lookup"><span data-stu-id="cbc80-104">Specifically, the procedure and example use the **EnumWindows** function to step through the list of windows and a managed callback function (named CallBack) to print the value of the window handle.</span></span>  
  
### <a name="to-implement-a-callback-function"></a><span data-ttu-id="cbc80-105">コールバック関数を実装するには</span><span class="sxs-lookup"><span data-stu-id="cbc80-105">To implement a callback function</span></span>  
  
1.  <span data-ttu-id="cbc80-106">実装を進める前に、**EnumWindows** 関数のシグネチャを見てみます。</span><span class="sxs-lookup"><span data-stu-id="cbc80-106">Look at the signature for the **EnumWindows** function before going further with the implementation.</span></span> <span data-ttu-id="cbc80-107">**EnumWindows** のシグネチャは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cbc80-107">**EnumWindows** has the following signature:</span></span>  
  
    ```  
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)  
    ```  
  
     <span data-ttu-id="cbc80-108">この関数がコールバックを必要とする 1 つの手掛かりは、**lpEnumFunc** 引数が存在することです。</span><span class="sxs-lookup"><span data-stu-id="cbc80-108">One clue that this function requires a callback is the presence of the **lpEnumFunc** argument.</span></span> <span data-ttu-id="cbc80-109">コールバック関数へのポインターを使用する引数の名前では、**lp** (long pointer) プレフィックスが **Func** サフィックスと組み合わされているのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="cbc80-109">It is common to see the **lp** (long pointer) prefix combined with the **Func** suffix in the name of arguments that take a pointer to a callback function.</span></span> <span data-ttu-id="cbc80-110">Win32 の関数に関するドキュメントについては、Microsoft プラットフォーム SDK を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cbc80-110">For documentation about Win32 functions, see the Microsoft Platform SDK.</span></span>  
  
2.  <span data-ttu-id="cbc80-111">マネージ コールバック関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="cbc80-111">Create the managed callback function.</span></span> <span data-ttu-id="cbc80-112">この例では、`CallBack` というデリゲート型を宣言しています。この型は 2 つの引数 (**hwnd** と **lparam**) を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="cbc80-112">The example declares a delegate type, called `CallBack`, which takes two arguments (**hwnd** and **lparam**).</span></span> <span data-ttu-id="cbc80-113">最初の引数はウィンドウのハンドル、2 番目の引数はアプリケーションで定義します。</span><span class="sxs-lookup"><span data-stu-id="cbc80-113">The first argument is a handle to the window; the second argument is application-defined.</span></span> <span data-ttu-id="cbc80-114">このリリースでは、両方の引数が整数でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="cbc80-114">In this release, both arguments must be integers.</span></span>  
  
     <span data-ttu-id="cbc80-115">コールバック関数は通常、成功を示す場合は 0 以外の値を返し、失敗を示す場合は 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="cbc80-115">Callback functions generally return nonzero values to indicate success and zero to indicate failure.</span></span> <span data-ttu-id="cbc80-116">この例では、列挙を続けるために戻り値を明示的に **true** に設定します。</span><span class="sxs-lookup"><span data-stu-id="cbc80-116">This example explicitly sets the return value to **true** to continue the enumeration.</span></span>  
  
3.  <span data-ttu-id="cbc80-117">デリゲートを作成し、**EnumWindows** 関数に引数として渡します。</span><span class="sxs-lookup"><span data-stu-id="cbc80-117">Create a delegate and pass it as an argument to the **EnumWindows** function.</span></span> <span data-ttu-id="cbc80-118">プラットフォーム呼び出しにより、デリゲートは既知のコールバック形式に自動的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="cbc80-118">Platform invoke converts the delegate to a familiar callback format automatically.</span></span>  
  
4.  <span data-ttu-id="cbc80-119">コールバック関数がその作業を完了する前にガベージ コレクターがデリゲートをクリアしないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="cbc80-119">Ensure that the garbage collector does not reclaim the delegate before the callback function completes its work.</span></span> <span data-ttu-id="cbc80-120">デリゲートをパラメーターとして渡した場合、または構造内のフィールドとして含まれるデリゲートを渡した場合、デリゲートは呼び出しの間収集されないままです。</span><span class="sxs-lookup"><span data-stu-id="cbc80-120">When you pass a delegate as a parameter, or pass a delegate contained as a field in a structure, it remains uncollected for the duration of the call.</span></span> <span data-ttu-id="cbc80-121">したがって、次の列挙例と同様に、コールバック関数はその作業を呼び出しが戻る前に完了するので、マネージ呼び出し元による追加操作を必要としません。</span><span class="sxs-lookup"><span data-stu-id="cbc80-121">So, as is the case in the following enumeration example, the callback function completes its work before the call returns and requires no additional action by the managed caller.</span></span>  
  
     <span data-ttu-id="cbc80-122">ただし、呼び出しが戻った後にコールバック関数を呼び出せる場合、マネージ呼び出し元は、コールバック関数が終了するまでデリゲートが収集されないようにしておくための対策を講じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="cbc80-122">If, however, the callback function can be invoked after the call returns, the managed caller must take steps to ensure that the delegate remains uncollected until the callback function finishes.</span></span> <span data-ttu-id="cbc80-123">ガベージ コレクションを回避する方法の詳細については、プラットフォーム呼び出しによる「[相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cbc80-123">For detailed information about preventing garbage collection, see [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md) with Platform Invoke.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbc80-124">例</span><span class="sxs-lookup"><span data-stu-id="cbc80-124">Example</span></span>  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
  
Public Delegate Function CallBack( _  
hwnd As Integer, lParam As Integer) As Boolean  
  
Public Class EnumReportApp  
  
    Declare Function EnumWindows Lib "user32" ( _  
       x As CallBack, y As Integer) As Integer  
  
    Public Shared Sub Main()  
        EnumWindows(AddressOf EnumReportApp.Report, 0)  
    End Sub 'Main  
  
    Public Shared Function Report(hwnd As Integer, lParam As Integer) _  
    As Boolean  
        Console.Write("Window handle is ")  
        Console.WriteLine(hwnd)  
        Return True  
    End Function 'Report  
End Class 'EnumReportApp  
```  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public delegate bool CallBack(int hwnd, int lParam);  
  
public class EnumReportApp  
{  
    [DllImport("user32")]  
    public static extern int EnumWindows(CallBack x, int y);   
  
    public static void Main()   
    {  
        CallBack myCallBack = new CallBack(EnumReportApp.Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    public static bool Report(int hwnd, int lParam)  
    {   
        Console.Write("Window handle is ");  
        Console.WriteLine(hwnd);  
        return true;  
    }  
}  
```  
  
```cpp  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
// A delegate type.  
delegate bool CallBack(int hwnd, int lParam);  
  
// Managed type with the method to call.  
ref class EnumReport  
{  
// Report the window handle.  
public:  
    [DllImport("user32")]  
    static int EnumWindows(CallBack^ x, int y);  
  
    static void Main()  
    {  
        EnumReport^ er = gcnew EnumReport;  
        CallBack^ myCallBack = gcnew CallBack(&EnumReport::Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    static bool Report(int hwnd, int lParam)  
    {  
       Console::Write(L"Window handle is ");  
       Console::WriteLine(hwnd);  
       return true;  
    }  
};  
  
int main()  
{  
    EnumReport::Main();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbc80-125">参照</span><span class="sxs-lookup"><span data-stu-id="cbc80-125">See Also</span></span>  
 [<span data-ttu-id="cbc80-126">コールバック関数</span><span class="sxs-lookup"><span data-stu-id="cbc80-126">Callback Functions</span></span>](../../../docs/framework/interop/callback-functions.md)  
 [<span data-ttu-id="cbc80-127">DLL 関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="cbc80-127">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
