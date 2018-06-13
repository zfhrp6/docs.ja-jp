---
title: エントリ ポイントの指定
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31bb28b5bda51fb1579021e47b8d5ec49adb644e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388834"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="54149-102">エントリ ポイントの指定</span><span class="sxs-lookup"><span data-stu-id="54149-102">Specifying an Entry Point</span></span>
<span data-ttu-id="54149-103">エントリ ポイントは、DLL 内の関数の位置を識別します。</span><span class="sxs-lookup"><span data-stu-id="54149-103">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="54149-104">マネージ プロジェクト内では、対象となる関数の元の名前または序数エントリ ポイントによって、その関数が相互運用の境界にまたがって識別されます。</span><span class="sxs-lookup"><span data-stu-id="54149-104">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="54149-105">また、エントリ ポイントを別の名前に割り当てて、関数の名前を事実上変更できます。</span><span class="sxs-lookup"><span data-stu-id="54149-105">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="54149-106">DLL 関数の名前を変更する理由を次に示します。</span><span class="sxs-lookup"><span data-stu-id="54149-106">Following is a list of possible reasons to rename a DLL function:</span></span>  
  
-   <span data-ttu-id="54149-107">大文字と小文字が区別される API 関数名を使わないようにするため</span><span class="sxs-lookup"><span data-stu-id="54149-107">To avoid using case-sensitive API function names</span></span>  
  
-   <span data-ttu-id="54149-108">既存の名前付け標準に合わせるため</span><span class="sxs-lookup"><span data-stu-id="54149-108">To comply with existing naming standards</span></span>  
  
-   <span data-ttu-id="54149-109">異なるデータ型を受け取る複数の関数を共存させるため (同じ DLL 関数の複数のバージョンを宣言することによって)</span><span class="sxs-lookup"><span data-stu-id="54149-109">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
-   <span data-ttu-id="54149-110">ANSI バージョンと Unicode バージョンを持つ API の使用を簡単にするため</span><span class="sxs-lookup"><span data-stu-id="54149-110">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="54149-111">このトピックでは、マネージ コード内の DLL 関数の名前を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="54149-111">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="54149-112">Visual Basic での関数名の変更</span><span class="sxs-lookup"><span data-stu-id="54149-112">Renaming a Function in Visual Basic</span></span>  
 <span data-ttu-id="54149-113">Visual Basic で <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> フィールドを設定するには、**Declare** ステートメントで **Function** キーワードを使います。</span><span class="sxs-lookup"><span data-stu-id="54149-113">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="54149-114">基本的な宣言を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="54149-114">The following example shows a basic declaration.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
 <span data-ttu-id="54149-115">定義に **Alias** キーワードを含めることで、**MessageBox** エントリ ポイントを **MsgBox** に置き換えることができます。その例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="54149-115">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="54149-116">どちらの例でも、**Auto** キーワードを使って、エントリ ポイントの文字セットのバージョンを指定する手間を省いています。</span><span class="sxs-lookup"><span data-stu-id="54149-116">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="54149-117">文字セットの選択の詳細については、「[文字セットの指定](../../../docs/framework/interop/specifying-a-character-set.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54149-117">For more information about selecting a character set, see [Specifying a Character Set](../../../docs/framework/interop/specifying-a-character-set.md).</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MsgBox Lib "user32.dll" _  
       Alias "MessageBox" (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="54149-118">C# および C++ での関数名の変更</span><span class="sxs-lookup"><span data-stu-id="54149-118">Renaming a Function in C# and C++</span></span>  
 <span data-ttu-id="54149-119">DLL 関数を名前または序数で指定するには、<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> フィールドを使います。</span><span class="sxs-lookup"><span data-stu-id="54149-119">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="54149-120">メソッド定義内の関数の名前が DLL 内のエントリ ポイントと同じである場合は、その関数を **EntryPoint** フィールドで明示的に識別する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="54149-120">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="54149-121">同じでない場合は、次のいずれかの属性書式を使って、名前または序数を指示します。</span><span class="sxs-lookup"><span data-stu-id="54149-121">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```  
[DllImport("dllname", EntryPoint="Functionname")]  
[DllImport("dllname", EntryPoint="#123")]  
```  
  
 <span data-ttu-id="54149-122">序数の前にシャープ記号 (#) を付ける必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="54149-122">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="54149-123">**EntryPoint** フィールドを使ってコード内の **MessageBoxA** を **MsgBox** に置き換える方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="54149-123">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
```csharp  
using System.Runtime.InteropServices;  
  
public class Win32 {  
    [DllImport("user32.dll", EntryPoint="MessageBoxA")]  
    public static extern int MsgBox(int hWnd, String text, String caption,  
                                    uint type);  
}  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
  
typedef void* HWND;  
[DllImport("user32", EntryPoint="MessageBoxA")]  
extern "C" int MsgBox(HWND hWnd,  
                      String*  pText,  
                      String*  pCaption,  
                      unsigned int uType);  
```  
  
## <a name="see-also"></a><span data-ttu-id="54149-124">参照</span><span class="sxs-lookup"><span data-stu-id="54149-124">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="54149-125">マネージ コードでのプロトタイプの作成</span><span class="sxs-lookup"><span data-stu-id="54149-125">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="54149-126">プラットフォーム呼び出しの例</span><span class="sxs-lookup"><span data-stu-id="54149-126">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="54149-127">プラットフォーム呼び出しによるデータのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="54149-127">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
