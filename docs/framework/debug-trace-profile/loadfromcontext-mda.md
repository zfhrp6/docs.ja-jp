---
title: loadFromContext MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: acd8291eda97caee72de4632f8715e6211deb7a3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="38792-102">loadFromContext MDA</span><span class="sxs-lookup"><span data-stu-id="38792-102">loadFromContext MDA</span></span>
<span data-ttu-id="38792-103">アセンブリが `LoadFrom` コンテキストに読み込まれると、`loadFromContext` マネージ デバッグ アシスタント (MDA) がアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="38792-103">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="38792-104">このような状況は、<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> または他の同様のメソッドを呼び出した結果として発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="38792-104">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="38792-105">症状</span><span class="sxs-lookup"><span data-stu-id="38792-105">Symptoms</span></span>  
 <span data-ttu-id="38792-106">一部のローダー メソッドは、使用すると、`LoadFrom` コンテキストでアセンブリが呼び出される結果になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="38792-106">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="38792-107">このコンテキストを使用すると、シリアル化、キャスティング、依存関係の解決について予期しない結果になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="38792-107">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="38792-108">一般的に、このような問題を回避するために、アセンブリを `Load` コンテキストに読み込むことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="38792-108">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="38792-109">この MDA を使用せずに、アセンブリが読み込まれたコンテキストを判断することは困難です。</span><span class="sxs-lookup"><span data-stu-id="38792-109">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="38792-110">原因</span><span class="sxs-lookup"><span data-stu-id="38792-110">Cause</span></span>  
 <span data-ttu-id="38792-111">一般的に、アセンブリは `Load` コンテキスト以外のパス (グローバル アセンブリ キャッシュや <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> プロパティなど) から読み込まれた場合、`LoadFrom` コンテキストに読み込まれていました。</span><span class="sxs-lookup"><span data-stu-id="38792-111">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="38792-112">解像度</span><span class="sxs-lookup"><span data-stu-id="38792-112">Resolution</span></span>  
 <span data-ttu-id="38792-113"><xref:System.Reflection.Assembly.LoadFrom%2A> の呼び出しが不要になるようにアプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="38792-113">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="38792-114">そのためには、次の手法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="38792-114">You can use the following techniques for doing so:</span></span>  
  
-   <span data-ttu-id="38792-115">グローバル アセンブリ キャッシュにアセンブリをインストールします。</span><span class="sxs-lookup"><span data-stu-id="38792-115">Install assemblies in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="38792-116">アセンブリを <xref:System.AppDomain> の <xref:System.AppDomainSetup.ApplicationBase%2A> ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="38792-116">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="38792-117">既定のドメインの場合、<xref:System.AppDomainSetup.ApplicationBase%2A> ディレクトリは、プロセスを開始した実行可能ファイルを含むディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="38792-117">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="38792-118">また、アセンブリを移動したくない場合は、必要に応じて新しい <xref:System.AppDomain> を作成します。</span><span class="sxs-lookup"><span data-stu-id="38792-118">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
-   <span data-ttu-id="38792-119">依存するアセンブリが、実行可能ファイルの相対的な子ディレクトリ内にある場合、アプリケーション構成 (.config) ファイルまたはセカンダリ アプリケーション ドメインのプローブ パスを追加します。</span><span class="sxs-lookup"><span data-stu-id="38792-119">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="38792-120">いずれの場合でも、<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> メソッドを使用するようにコードを変更できます。</span><span class="sxs-lookup"><span data-stu-id="38792-120">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="38792-121">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="38792-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="38792-122">MDA は、CLR にまったく影響がありません。</span><span class="sxs-lookup"><span data-stu-id="38792-122">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="38792-123">MDA では、読み込み要求の結果として使用されたコンテキストが報告されます。</span><span class="sxs-lookup"><span data-stu-id="38792-123">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="38792-124">出力</span><span class="sxs-lookup"><span data-stu-id="38792-124">Output</span></span>  
 <span data-ttu-id="38792-125">MDA では、アセンブリが `LoadFrom` コンテキストに読み込まれたことが報告されます。</span><span class="sxs-lookup"><span data-stu-id="38792-125">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="38792-126">また、アセンブリの簡易名とパスが指定されます。</span><span class="sxs-lookup"><span data-stu-id="38792-126">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="38792-127">`LoadFrom` コンテキストの使用を回避する軽減策も提案されます。</span><span class="sxs-lookup"><span data-stu-id="38792-127">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="38792-128">構成</span><span class="sxs-lookup"><span data-stu-id="38792-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="38792-129">例</span><span class="sxs-lookup"><span data-stu-id="38792-129">Example</span></span>  
 <span data-ttu-id="38792-130">次のコードの例は、この MDA がアクティブ化されることのある状況を示しています。</span><span class="sxs-lookup"><span data-stu-id="38792-130">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```  
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is   
            // located outside of the Load context probing path.   
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="38792-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="38792-131">See Also</span></span>  
 [<span data-ttu-id="38792-132">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="38792-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
