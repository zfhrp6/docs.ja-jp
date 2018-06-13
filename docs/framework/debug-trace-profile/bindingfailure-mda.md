---
title: bindingFailure MDA
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a75efaf6703858fdb48a3f09635da1be4463d34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364701"
---
# <a name="bindingfailure-mda"></a><span data-ttu-id="5b6f0-102">bindingFailure MDA</span><span class="sxs-lookup"><span data-stu-id="5b6f0-102">bindingFailure MDA</span></span>
<span data-ttu-id="5b6f0-103">`bindingFailure` マネージ デバッグ アシスタント (MDA) は、アセンブリの読み込みに失敗したときにアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-103">The `bindingFailure` managed debugging assistant (MDA) is activated when an assembly fails to load.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5b6f0-104">現象</span><span class="sxs-lookup"><span data-stu-id="5b6f0-104">Symptoms</span></span>  
 <span data-ttu-id="5b6f0-105">コードは、静的参照またはいずれかのローダー メソッド (<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> や <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> など) を使用して、アセンブリを読み込もうとしました。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-105">Code has attempted to load an assembly using a static reference or one of the loader methods, such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5b6f0-106">アセンブリは読み込まれず、<xref:System.IO.FileNotFoundException> または <xref:System.IO.FileLoadException> 例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-106">The assembly is not loaded and a <xref:System.IO.FileNotFoundException> or <xref:System.IO.FileLoadException> exception is thrown.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5b6f0-107">原因</span><span class="sxs-lookup"><span data-stu-id="5b6f0-107">Cause</span></span>  
 <span data-ttu-id="5b6f0-108">バインディング エラーは、ランタイムがアセンブリを読み込むことができない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-108">A binding failure occurs when the runtime is unable to load an assembly.</span></span> <span data-ttu-id="5b6f0-109">バインディング エラーは、次のいずれかの状況の結果として発生することもあります。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-109">A binding failure might be the result of one of the following situations:</span></span>  
  
-   <span data-ttu-id="5b6f0-110">共通言語ランタイム (CLR) は、要求されたアセンブリを見つけることができません。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-110">The common language runtime (CLR) cannot find the requested assembly.</span></span> <span data-ttu-id="5b6f0-111">考えられる理由は多数あります。たとえば、アセンブリがインストールされていない、あるいはアプリケーションがアセンブリを見つけるように正しく構成されていないなどです。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-111">There are many reasons this can occur, such as the assembly not being installed or the application not being correctly configured to find the assembly.</span></span>  
  
-   <span data-ttu-id="5b6f0-112">一般的な問題のシナリオの場合、型は別のアプリケーション ドメインに渡されます。CLR は、他のアプリケーション ドメインにその型が含まれているアセンブリを読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-112">A common problem scenario is passing a type to another application domain, which requires the CLR to load the assembly containing that type in the other application domain.</span></span> <span data-ttu-id="5b6f0-113">他のアプリケーション ドメインが元のアプリケーション ドメインとは異なる構成の場合、ランタイムがアセンブリを読み込めないことがあります。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-113">It may not be possible for the runtime to load the assembly if the other application domain is configured differently from the original application domain.</span></span> <span data-ttu-id="5b6f0-114">たとえば、2 つのアプリケーション ドメインで、<xref:System.AppDomain.BaseDirectory%2A> プロパティ値が異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-114">For example, the two application domains might have different <xref:System.AppDomain.BaseDirectory%2A> property values.</span></span>  
  
-   <span data-ttu-id="5b6f0-115">要求されたアセンブリは、破損しているか、アセンブリではありません。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-115">The requested assembly is corrupted or is not an assembly.</span></span>  
  
-   <span data-ttu-id="5b6f0-116">アセンブリを読み込もうとしているコードには、アセンブリを読み込むための適切なコード アクセス セキュリティのアクセス許可が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-116">The code attempting to load the assembly does not have the correct code access security permissions to load assemblies.</span></span>  
  
-   <span data-ttu-id="5b6f0-117">ユーザー資格情報には、ファイルを読み取るために必要なアクセス許可が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-117">The user credentials do not provide the required permissions to read the file.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5b6f0-118">解像度</span><span class="sxs-lookup"><span data-stu-id="5b6f0-118">Resolution</span></span>  
 <span data-ttu-id="5b6f0-119">最初の手順は、要求されたアセンブリに CLR がバインドできなかった原因を特定することです。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-119">The first step is to determine why the CLR could not bind to the requested assembly.</span></span> <span data-ttu-id="5b6f0-120">たとえば、「原因」セクションに一覧表示されたシナリオのように、ランタイムが要求されたアセンブリを見つけられなかったり、読み込めなかったりする理由は多数あります。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-120">There are many reasons why the runtime might not have found or been able load the requested assembly, such as the scenarios listed in the Cause section.</span></span> <span data-ttu-id="5b6f0-121">バインディング エラーの原因を除去するには、次のアクションをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-121">The following actions are recommended to eliminate the cause of the binding failure:</span></span>  
  
-   <span data-ttu-id="5b6f0-122">`bindingFailure` MDA によって提供されるデータを使用して、原因を特定します。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-122">Determine the cause by using the data provided by the `bindingFailure` MDA:</span></span>  
  
    -   <span data-ttu-id="5b6f0-123">アセンブリ バインダーによって生成されるエラー ログを読み取るために、[Fuslogvw.exe (アセンブリ バインディング ログ ビューアー)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) を実行します。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-123">Run the [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to read the error logs produced by the assembly binder.</span></span>  
  
    -   <span data-ttu-id="5b6f0-124">アセンブリが要求された位置にあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-124">Determine if the assembly is at the location requested.</span></span> <span data-ttu-id="5b6f0-125"><xref:System.Reflection.Assembly.LoadFrom%2A> および <xref:System.Reflection.Assembly.LoadFile%2A> メソッドの場合は、要求された位置を簡単に確認できます。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-125">In the case of the <xref:System.Reflection.Assembly.LoadFrom%2A> and <xref:System.Reflection.Assembly.LoadFile%2A> methods, the requested location can be easily determined.</span></span> <span data-ttu-id="5b6f0-126"><xref:System.Reflection.Assembly.Load%2A> メソッドの場合は、アセンブリ ID を使用してバインドするため、アプリケーション ドメインの <xref:System.AppDomain.BaseDirectory%2A> プロパティ プローブ パスおよびグローバル アセンブリ キャッシュで、アセンブリ ID と一致するアセンブリを検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-126">In the case of the <xref:System.Reflection.Assembly.Load%2A> method, which binds using the assembly identity, you must look for assemblies that match that identity in the application domain's <xref:System.AppDomain.BaseDirectory%2A> property probe path and the global assembly cache.</span></span>  
  
-   <span data-ttu-id="5b6f0-127">前の手順で確認した内容に基づいて、原因を解決します。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-127">Resolve the cause based on the preceding determination.</span></span> <span data-ttu-id="5b6f0-128">使用できる解決オプションは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-128">Possible resolution options are the following:</span></span>  
  
    -   <span data-ttu-id="5b6f0-129">要求されたアセンブリをグローバル アセンブリ キャッシュにインストールし、</span><span class="sxs-lookup"><span data-stu-id="5b6f0-129">Install the requested assembly in the global assembly cache and call the.</span></span> <span data-ttu-id="5b6f0-130"><xref:System.Reflection.Assembly.Load%2A> メソッドを呼び出して ID でアセンブリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-130"><xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>  
  
    -   <span data-ttu-id="5b6f0-131">要求されたアセンブリをアプリケーション ディレクトリにコピーし、<xref:System.Reflection.Assembly.Load%2A> メソッドを呼び出して ID でアセンブリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-131">Copy the requested assembly into the application directory and call the <xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>  
  
    -   <span data-ttu-id="5b6f0-132"><xref:System.AppDomain.BaseDirectory%2A> プロパティを変更するか、プライベート プローブ パスを追加して、バインディング エラーが発生したアプリケーション ドメインがアセンブリ パスを含むように再構成します。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-132">Reconfigure the application domain in which the binding failure occurred to include the assembly path by either changing the <xref:System.AppDomain.BaseDirectory%2A> property or adding private probing paths.</span></span>  
  
    -   <span data-ttu-id="5b6f0-133">ログオンしているユーザーがファイルを読み取れるように、ファイルのアクセス制御リストを変更します。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-133">Change the access control list for the file to allow the logged-on user to read the file.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5b6f0-134">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="5b6f0-134">Effect on the Runtime</span></span>  
 <span data-ttu-id="5b6f0-135">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-135">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="5b6f0-136">バインディング エラーに関するデータを報告するだけです。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-136">It only reports data about binding failures.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5b6f0-137">出力</span><span class="sxs-lookup"><span data-stu-id="5b6f0-137">Output</span></span>  
 <span data-ttu-id="5b6f0-138">MDA は、読み込みに失敗したアセンブリを報告します。これには、要求されたパスや表示名、バインディング コンテキスト、読み込みが要求されたアプリケーション ドメイン、エラーの理由などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-138">The MDA reports the assembly that failed to load, including the requested path and/or display name, the binding context, the application domain in which the load was requested, and the reason for the failure.</span></span>  
  
 <span data-ttu-id="5b6f0-139">表示名や要求されたパスは、そのデータが CLR で利用できなかった場合は空白である場合があります。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-139">The display name or requested path may be blank if that data was not available to the CLR.</span></span> <span data-ttu-id="5b6f0-140">失敗した呼び出しが <xref:System.Reflection.Assembly.Load%2A> メソッドに対するものであった場合は、ランタイムがアセンブリの表示名を判別できなかったことが考えられます。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-140">If the call that failed was to the <xref:System.Reflection.Assembly.Load%2A> method, it is likely the runtime could not determine the display name for the assembly.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5b6f0-141">構成</span><span class="sxs-lookup"><span data-stu-id="5b6f0-141">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <bindingFailure />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="5b6f0-142">例</span><span class="sxs-lookup"><span data-stu-id="5b6f0-142">Example</span></span>  
 <span data-ttu-id="5b6f0-143">次のコードの例は、この MDA がアクティブ化されることのある状況を示しています。</span><span class="sxs-lookup"><span data-stu-id="5b6f0-143">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // This call attempts to load a nonexistent assembly.  
            // The call will throw a System.IO.FileNotFound exception  
            // and cause the activation of the bindingFailure MDA   
            // if it is registered.  
            Assembly.Load("NonExistentAssembly");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b6f0-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b6f0-144">See Also</span></span>  
 [<span data-ttu-id="5b6f0-145">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="5b6f0-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
