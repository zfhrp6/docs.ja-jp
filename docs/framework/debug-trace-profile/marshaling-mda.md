---
title: marshaling MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3f92e849798f03702ca9a5eab3120067a651c999
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="marshaling-mda"></a><span data-ttu-id="5cb73-102">marshaling MDA</span><span class="sxs-lookup"><span data-stu-id="5cb73-102">marshaling MDA</span></span>
<span data-ttu-id="5cb73-103">`marshaling` マネージ デバッグ アシスタント (MDA: Managed Debugging Assistant) は、CLR がメソッドのパラメーターまたは構造体のフィールドに関するマーシャリング情報を設定するとアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="5cb73-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="5cb73-104">この MDA は、JIT コンパイルされたアセンブリでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="5cb73-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5cb73-105">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="5cb73-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="5cb73-106">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="5cb73-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5cb73-107">出力</span><span class="sxs-lookup"><span data-stu-id="5cb73-107">Output</span></span>  
 <span data-ttu-id="5cb73-108">この MDA は、マネージ コンテキストとアンマネージ コンテキストのパラメーターまたはフィールドの型、およびその型を含む構造体またはメソッドを表示します。</span><span class="sxs-lookup"><span data-stu-id="5cb73-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="5cb73-109">フィールドの出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5cb73-109">The following is an example of the output for a field:</span></span>  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="5cb73-110">構成</span><span class="sxs-lookup"><span data-stu-id="5cb73-110">Configuration</span></span>  
 <span data-ttu-id="5cb73-111">この MDA の構成では、関連するフィールドまたはメソッドの名前を基にして、報告されたマーシャリング情報をフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="5cb73-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="5cb73-112">`methodFilter`、`fieldFilter`、および `match` の各要素を使用してフィルターを指定する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="5cb73-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="5cb73-113">`name` 属性をアスタリスク (*) に設定すると、すべてに一致します。</span><span class="sxs-lookup"><span data-stu-id="5cb73-113">Setting the `name` attribute to an asterisk (*) will match everything.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="Method1"/>  
        <match name="Method2"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="Field1"/>  
        <match name="Field2"/>  
       </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5cb73-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5cb73-114">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="5cb73-115">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="5cb73-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="5cb73-116">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="5cb73-116">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
