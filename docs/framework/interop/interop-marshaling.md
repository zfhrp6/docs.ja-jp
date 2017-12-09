---
title: "相互運用マーシャリング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, COM interop
- interop marshaling
- interop marshaling, about interop marshaling
ms.assetid: 115f7a2f-d422-4605-ab36-13a8dd28142a
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 381eccc42d5abb85cde618f4710f044f172295d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="interop-marshaling"></a><span data-ttu-id="d7674-102">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="d7674-102">Interop Marshaling</span></span>
<a name="top"></a> <span data-ttu-id="d7674-103">相互運用マーシャリングは、メソッド引数と戻り値によって、呼び出し中にマネージ メモリとアンマネージ メモリの間でデータを渡す方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="d7674-103">Interop marshaling governs how data is passed in method arguments and return values between managed and unmanaged memory during calls.</span></span> <span data-ttu-id="d7674-104">相互運用マーシャリングは、共通言語ランタイムのマーシャリング サービスによって実行される、ランタイム アクティビティです。</span><span class="sxs-lookup"><span data-stu-id="d7674-104">Interop marshaling is a run-time activity performed by the common language runtime's marshaling service.</span></span>  
  
 <span data-ttu-id="d7674-105">ほとんどのデータ型は、マネージとアンマネージの両方のメモリに共通の表現があります。</span><span class="sxs-lookup"><span data-stu-id="d7674-105">Most data types have common representations in both managed and unmanaged memory.</span></span> <span data-ttu-id="d7674-106">相互運用マーシャラーは、これらの型を処理します。</span><span class="sxs-lookup"><span data-stu-id="d7674-106">The interop marshaler handles these types for you.</span></span> <span data-ttu-id="d7674-107">その他の型は、あいまいな型であるか、マネージ メモリでまったく表現されていない型である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d7674-107">Other types can be ambiguous or not represented at all in managed memory.</span></span>  
  
 <span data-ttu-id="d7674-108">あいまいな型は、複数のアンマネージ表現が 1 つのマネージ型にマップされていたり、配列のサイズなどの型情報が欠落していたりします。</span><span class="sxs-lookup"><span data-stu-id="d7674-108">An ambiguous type can have either multiple unmanaged representations that map to a single managed type, or missing type information, such as the size of an array.</span></span> <span data-ttu-id="d7674-109">あいまいな型の場合、マーシャラーは、既定の表現と複数の表現が存在するときのための代替表現とを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7674-109">For ambiguous types, the marshaler provides a default representation and alternative representations where multiple representations exist.</span></span> <span data-ttu-id="d7674-110">あいまいな型をマーシャリングする方法について、マーシャラーに明示的な指示を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="d7674-110">You can supply explicit instructions to the marshaler on how it is to marshal an ambiguous type.</span></span>  
  
 <span data-ttu-id="d7674-111">この概要は、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="d7674-111">This overview contains the following sections:</span></span>  
  
-   [<span data-ttu-id="d7674-112">プラットフォーム呼び出しと COM 相互運用のモデル</span><span class="sxs-lookup"><span data-stu-id="d7674-112">Platform Invoke and COM Interop Models</span></span>](#platform_invoke_and_com_interop_models)  
  
-   [<span data-ttu-id="d7674-113">マーシャリングと COM アパートメント</span><span class="sxs-lookup"><span data-stu-id="d7674-113">Marshaling and COM Apartments</span></span>](#marshaling_and_com_apartments)  
  
-   [<span data-ttu-id="d7674-114">リモートの呼び出しのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="d7674-114">Marshaling Remote Calls</span></span>](#marshaling_remote_calls)  
  
-   [<span data-ttu-id="d7674-115">関連トピック</span><span class="sxs-lookup"><span data-stu-id="d7674-115">Related Topics</span></span>](#related_topics)  
  
-   [<span data-ttu-id="d7674-116">参照</span><span class="sxs-lookup"><span data-stu-id="d7674-116">Reference</span></span>](#reference)  
  
<a name="platform_invoke_and_com_interop_models"></a>   
## <a name="platform-invoke-and-com-interop-models"></a><span data-ttu-id="d7674-117">プラットフォーム呼び出しと COM 相互運用のモデル</span><span class="sxs-lookup"><span data-stu-id="d7674-117">Platform Invoke and COM Interop Models</span></span>  
 <span data-ttu-id="d7674-118">共通言語ランタイムは、アンマネージ コードと相互運用するために、次の 2 つのメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7674-118">The common language runtime provides two mechanisms for interoperating with unmanaged code:</span></span>  
  
-   <span data-ttu-id="d7674-119">プラットフォーム呼び出しにより、マネージ コードは、アンマネージ ライブラリからエクスポートされた関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="d7674-119">Platform invoke, which enables managed code to call functions exported from an unmanaged library.</span></span>  
  
-   <span data-ttu-id="d7674-120">COM 相互運用により、マネージ コードは、インターフェイスを介してコンポーネント オブジェクト モデル (COM) オブジェクトと対話できます。</span><span class="sxs-lookup"><span data-stu-id="d7674-120">COM interop, which enables managed code to interact with Component Object Model (COM) objects through interfaces.</span></span>  
  
 <span data-ttu-id="d7674-121">プラットフォーム呼び出しと COM 相互運用はどちらも、必要な場合に、相互運用マーシャリングを使用して呼び出し元と呼び出し先との間でメソッド引数を正確に移動します。</span><span class="sxs-lookup"><span data-stu-id="d7674-121">Both platform invoke and COM interop use interop marshaling to accurately move method arguments between caller and callee and back, if required.</span></span> <span data-ttu-id="d7674-122">次の図が示すように、プラットフォーム呼び出しメソッドの呼び出しはマネージ コードからアンマネージ コードにフローして、[コールバック関数](../../../docs/framework/interop/callback-functions.md)が関係していない限りその逆の方向にはフローしません。</span><span class="sxs-lookup"><span data-stu-id="d7674-122">As the following illustration shows, a platform invoke method call flows from managed to unmanaged code and never the other way, except when [callback functions](../../../docs/framework/interop/callback-functions.md) are involved.</span></span> <span data-ttu-id="d7674-123">プラットフォーム呼び出しの呼び出しはマネージ コードからアンマネージ コードにのみフローしますが、データは入出力パラメーターとして双方向にフローできます。</span><span class="sxs-lookup"><span data-stu-id="d7674-123">Even though platform invoke calls can flow only from managed to unmanaged code, data can flow in both directions as input or output parameters.</span></span> <span data-ttu-id="d7674-124">COM 相互運用のメソッド呼び出しは、どちらの方向にもフローできます。</span><span class="sxs-lookup"><span data-stu-id="d7674-124">COM interop method calls can flow in either direction.</span></span>  
  
 <span data-ttu-id="d7674-125">![プラットフォーム呼び出し](../../../docs/framework/interop/media/interopmarshaling.png "interopmarshaling")</span><span class="sxs-lookup"><span data-stu-id="d7674-125">![Platform invoke](../../../docs/framework/interop/media/interopmarshaling.png "interopmarshaling")</span></span>  
<span data-ttu-id="d7674-126">プラットフォーム呼び出しと COM 相互運用の呼び出しフロー</span><span class="sxs-lookup"><span data-stu-id="d7674-126">Platform invoke and COM interop call flow</span></span>  
  
 <span data-ttu-id="d7674-127">最下位のレベルでは、どちらのメカニズムも同じ相互運用マーシャリング サービスを使用します。ただし、特定のデータ型は、COM 相互運用またはプラットフォーム呼び出しでのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d7674-127">At the lowest level, both mechanisms use the same interop marshaling service; however, certain data types are supported exclusively by COM interop or platform invoke.</span></span> <span data-ttu-id="d7674-128">詳しくは、「[既定のマーシャリング動作](../../../docs/framework/interop/default-marshaling-behavior.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7674-128">For details, see [Default Marshaling Behavior](../../../docs/framework/interop/default-marshaling-behavior.md).</span></span>  
  
 [<span data-ttu-id="d7674-129">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="d7674-129">Back to top</span></span>](#top)  
  
<a name="marshaling_and_com_apartments"></a>   
## <a name="marshaling-and-com-apartments"></a><span data-ttu-id="d7674-130">マーシャリングと COM アパートメント</span><span class="sxs-lookup"><span data-stu-id="d7674-130">Marshaling and COM Apartments</span></span>  
 <span data-ttu-id="d7674-131">相互運用マーシャラーは、共通言語ランタイム ヒープとアンマネージ ヒープの間でデータをマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="d7674-131">The interop marshaler marshals data between the common language runtime heap and the unmanaged heap.</span></span> <span data-ttu-id="d7674-132">呼び出し元と呼び出し先がデータの同じインスタンスで機能できないときには常に、マーシャリングが生じます。</span><span class="sxs-lookup"><span data-stu-id="d7674-132">Marshaling occurs whenever the caller and callee cannot operate on the same instance of data.</span></span> <span data-ttu-id="d7674-133">相互運用マーシャラーにより、呼び出し元と呼び出し先がデータの独自のコピーを持っている場合でも、見かけ上は同じデータに対して機能しているようにすることが可能になります。</span><span class="sxs-lookup"><span data-stu-id="d7674-133">The interop marshaler makes it possible for the caller and callee to appear to be operating on the same data even if they have their own copy of the data.</span></span>  
  
 <span data-ttu-id="d7674-134">COM には、COM アパートメント間や異なる COM プロセス間でデータをマーシャリングするマーシャラーもあります。</span><span class="sxs-lookup"><span data-stu-id="d7674-134">COM also has a marshaler that marshals data between COM apartments or different COM processes.</span></span> <span data-ttu-id="d7674-135">同じ COM アパートメント内でマネージ コードとアンマネージ コード間の呼び出しをする場合は、相互運用マーシャラーが関連する唯一のマーシャラーとなります。</span><span class="sxs-lookup"><span data-stu-id="d7674-135">When calling between managed and unmanaged code within the same COM apartment, the interop marshaler is the only marshaler involved.</span></span> <span data-ttu-id="d7674-136">異なる COM アパートメントや異なるプロセス内でマネージ コードとアンマネージ コード間の呼び出しをする場合は、相互運用マーシャラーと COM マーシャラーの両方が関連します。</span><span class="sxs-lookup"><span data-stu-id="d7674-136">When calling between managed code and unmanaged code in a different COM apartment or a different process, both the interop marshaler and the COM marshaler are involved.</span></span>  
  
### <a name="com-clients-and-managed-servers"></a><span data-ttu-id="d7674-137">COM クライアントとマネージ サーバー</span><span class="sxs-lookup"><span data-stu-id="d7674-137">COM Clients and Managed Servers</span></span>  
 <span data-ttu-id="d7674-138">[Regasm.exe (アセンブリ登録ツール)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) によって登録されたタイプ ライブラリのあるエクスポートされたマネージ サーバーでは、`ThreadingModel` レジストリ エントリが `Both` に設定されています。</span><span class="sxs-lookup"><span data-stu-id="d7674-138">An exported managed server with a type library registered by the [Regasm.exe (Assembly Registration Tool)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) has a `ThreadingModel` registry entry set to `Both`.</span></span> <span data-ttu-id="d7674-139">この値は、シングルスレッド アパートメント (STA) またはマルチスレッド アパートメント (MTA) で、サーバーをアクティブ化できることを示します。</span><span class="sxs-lookup"><span data-stu-id="d7674-139">This value indicates that the server can be activated in a single-threaded apartment (STA) or a multithreaded apartment (MTA).</span></span> <span data-ttu-id="d7674-140">次の表に示すように、サーバー オブジェクトは、その呼び出し元と同じアパートメント内に作成されます。</span><span class="sxs-lookup"><span data-stu-id="d7674-140">The server object is created in the same apartment as its caller, as shown in the following table.</span></span>  
  
|<span data-ttu-id="d7674-141">COM クライアント</span><span class="sxs-lookup"><span data-stu-id="d7674-141">COM client</span></span>|<span data-ttu-id="d7674-142">.NET サーバー</span><span class="sxs-lookup"><span data-stu-id="d7674-142">.NET server</span></span>|<span data-ttu-id="d7674-143">マーシャリングの要件</span><span class="sxs-lookup"><span data-stu-id="d7674-143">Marshaling requirements</span></span>|  
|----------------|-----------------|-----------------------------|  
|<span data-ttu-id="d7674-144">STA</span><span class="sxs-lookup"><span data-stu-id="d7674-144">STA</span></span>|<span data-ttu-id="d7674-145">`Both` は STA になります。</span><span class="sxs-lookup"><span data-stu-id="d7674-145">`Both` becomes STA.</span></span>|<span data-ttu-id="d7674-146">同じアパートメントでのマーシャリング。</span><span class="sxs-lookup"><span data-stu-id="d7674-146">Same-apartment marshaling.</span></span>|  
|<span data-ttu-id="d7674-147">MTA</span><span class="sxs-lookup"><span data-stu-id="d7674-147">MTA</span></span>|<span data-ttu-id="d7674-148">`Both` は MTA になります。</span><span class="sxs-lookup"><span data-stu-id="d7674-148">`Both` becomes MTA.</span></span>|<span data-ttu-id="d7674-149">同じアパートメントでのマーシャリング。</span><span class="sxs-lookup"><span data-stu-id="d7674-149">Same-apartment marshaling.</span></span>|  
  
 <span data-ttu-id="d7674-150">クライアントとサーバーが同じアパートメント内にあるため、相互運用マーシャリング サービスはすべてのデータのマーシャリングを自動的に処理します。</span><span class="sxs-lookup"><span data-stu-id="d7674-150">Because the client and server are in the same apartment, the interop marshaling service automatically handles all data marshaling.</span></span> <span data-ttu-id="d7674-151">次の図は、同じ COM スタイル アパートメント内のマネージ ヒープとアンマネージ ヒープの間で機能している、相互運用マーシャリング サービスを示しています。</span><span class="sxs-lookup"><span data-stu-id="d7674-151">The following illustration shows the interop marshaling service operating between managed and unmanaged heaps within the same COM-style apartment.</span></span>  
  
 <span data-ttu-id="d7674-152">![相互運用マーシャリング](../../../docs/framework/interop/media/interopheap.gif "interopheap")</span><span class="sxs-lookup"><span data-stu-id="d7674-152">![Interop marshaling](../../../docs/framework/interop/media/interopheap.gif "interopheap")</span></span>  
<span data-ttu-id="d7674-153">同じアパートメントでのマーシャリングのプロセス</span><span class="sxs-lookup"><span data-stu-id="d7674-153">Same-apartment marshaling process</span></span>  
  
 <span data-ttu-id="d7674-154">マネージ サーバーをエクスポートする予定の場合は、サーバーのアパートメントが COM クライアントによって決定されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d7674-154">If you plan to export a managed server, be aware that the COM client determines the apartment of the server.</span></span> <span data-ttu-id="d7674-155">MTA 内で初期化された COM クライアントから呼び出されるマネージ サーバーは、スレッド セーフを確保する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7674-155">A managed server called by a COM client initialized in an MTA must ensure thread safety.</span></span>  
  
### <a name="managed-clients-and-com-servers"></a><span data-ttu-id="d7674-156">マネージ クライアントと COM サーバー</span><span class="sxs-lookup"><span data-stu-id="d7674-156">Managed Clients and COM Servers</span></span>  
 <span data-ttu-id="d7674-157">マネージ クライアントのアパートメントの既定の設定は MTA です。ただし、.NET クライアントのアプリケーションの種類によっては、既定の設定が変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="d7674-157">The default setting for managed client apartments is MTA; however, the application type of the .NET client can change the default setting.</span></span> <span data-ttu-id="d7674-158">たとえば、[!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] クライアントのアパートメントの設定は STA です。</span><span class="sxs-lookup"><span data-stu-id="d7674-158">For example, a [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] client apartment setting is STA.</span></span> <span data-ttu-id="d7674-159"><xref:System.STAThreadAttribute?displayProperty=nameWithType>、<xref:System.MTAThreadAttribute?displayProperty=nameWithType>、<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> プロパティ、または <xref:System.Web.UI.Page.AspCompatMode%2A?displayProperty=nameWithType> プロパティを使用して、マネージ クライアントのアパートメントの設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="d7674-159">You can use the <xref:System.STAThreadAttribute?displayProperty=nameWithType>, the <xref:System.MTAThreadAttribute?displayProperty=nameWithType>, the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property, or the <xref:System.Web.UI.Page.AspCompatMode%2A?displayProperty=nameWithType> property to examine and change the apartment setting of a managed client.</span></span>  
  
 <span data-ttu-id="d7674-160">コンポーネントの作成者は、COM サーバーのスレッド アフィニティを設定します。</span><span class="sxs-lookup"><span data-stu-id="d7674-160">The author of the component sets the thread affinity of a COM server.</span></span> <span data-ttu-id="d7674-161">次の表は、.NET クライアントと COM サーバーのアパートメント設定の組み合わせを示しています。</span><span class="sxs-lookup"><span data-stu-id="d7674-161">The following table shows the combinations of apartment settings for .NET clients and COM servers.</span></span> <span data-ttu-id="d7674-162">また、結果として生じる、組み合わせのためのマーシャリング要件も示しています。</span><span class="sxs-lookup"><span data-stu-id="d7674-162">It also shows the resulting marshaling requirements for the combinations.</span></span>  
  
|<span data-ttu-id="d7674-163">.NET クライアント</span><span class="sxs-lookup"><span data-stu-id="d7674-163">.NET client</span></span>|<span data-ttu-id="d7674-164">COM サーバー</span><span class="sxs-lookup"><span data-stu-id="d7674-164">COM server</span></span>|<span data-ttu-id="d7674-165">マーシャリングの要件</span><span class="sxs-lookup"><span data-stu-id="d7674-165">Marshaling requirements</span></span>|  
|-----------------|----------------|-----------------------------|  
|<span data-ttu-id="d7674-166">MTA (既定)</span><span class="sxs-lookup"><span data-stu-id="d7674-166">MTA (default)</span></span>|<span data-ttu-id="d7674-167">MTA</span><span class="sxs-lookup"><span data-stu-id="d7674-167">MTA</span></span><br /><br /> <span data-ttu-id="d7674-168">STA</span><span class="sxs-lookup"><span data-stu-id="d7674-168">STA</span></span>|<span data-ttu-id="d7674-169">相互運用マーシャリング。</span><span class="sxs-lookup"><span data-stu-id="d7674-169">Interop marshaling.</span></span><br /><br /> <span data-ttu-id="d7674-170">相互運用と COM マーシャリング。</span><span class="sxs-lookup"><span data-stu-id="d7674-170">Interop and COM marshaling.</span></span>|  
|<span data-ttu-id="d7674-171">STA</span><span class="sxs-lookup"><span data-stu-id="d7674-171">STA</span></span>|<span data-ttu-id="d7674-172">MTA</span><span class="sxs-lookup"><span data-stu-id="d7674-172">MTA</span></span><br /><br /> <span data-ttu-id="d7674-173">STA</span><span class="sxs-lookup"><span data-stu-id="d7674-173">STA</span></span>|<span data-ttu-id="d7674-174">相互運用と COM マーシャリング。</span><span class="sxs-lookup"><span data-stu-id="d7674-174">Interop and COM marshaling.</span></span><br /><br /> <span data-ttu-id="d7674-175">相互運用マーシャリング。</span><span class="sxs-lookup"><span data-stu-id="d7674-175">Interop marshaling.</span></span>|  
  
 <span data-ttu-id="d7674-176">マネージ クライアントとアンマネージ サーバーが同じアパートメント内にあるとき、相互運用マーシャリング サービスはすべてのデータのマーシャリングを処理します。</span><span class="sxs-lookup"><span data-stu-id="d7674-176">When a managed client and unmanaged server are in the same apartment, the interop marshaling service handles all data marshaling.</span></span> <span data-ttu-id="d7674-177">ただし、クライアントとサーバーが異なるアパートメント内で初期化される場合は、COM マーシャリングも必要となります。</span><span class="sxs-lookup"><span data-stu-id="d7674-177">However, when client and server are initialized in different apartments, COM marshaling is also required.</span></span> <span data-ttu-id="d7674-178">次の図は、アパートメント間の呼び出しの要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="d7674-178">The following illustration shows the elements of a cross-apartment call.</span></span>  
  
 <span data-ttu-id="d7674-179">![COM マーシャリング](../../../docs/framework/interop/media/singleprocessmultapt.gif "singleprocessmultapt")</span><span class="sxs-lookup"><span data-stu-id="d7674-179">![COM marshaling](../../../docs/framework/interop/media/singleprocessmultapt.gif "singleprocessmultapt")</span></span>  
<span data-ttu-id="d7674-180">.NET クライアントと COM オブジェクト間でのアパートメント間の呼び出し</span><span class="sxs-lookup"><span data-stu-id="d7674-180">Cross-apartment call between a .NET client and COM object</span></span>  
  
 <span data-ttu-id="d7674-181">アパートメント間のマーシャリングでは、次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="d7674-181">For cross-apartment marshaling, you can do the following:</span></span>  
  
-   <span data-ttu-id="d7674-182">アパートメント間のマーシャリングのオーバーヘッドを受け入れます。これは、境界を越える呼び出しが多くがある場合にのみ認識されます。</span><span class="sxs-lookup"><span data-stu-id="d7674-182">Accept the overhead of the cross-apartment marshaling, which is noticeable only when there are many calls across the boundary.</span></span> <span data-ttu-id="d7674-183">呼び出しがアパートメントの境界を正常に越えるようにするためには、COM コンポーネントのタイプ ライブラリを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7674-183">You must register the type library of the COM component for calls to successfully cross the apartment boundary.</span></span>  
  
-   <span data-ttu-id="d7674-184">クライアント スレッドを STA または MTA に設定して、メイン スレッドを変更します。</span><span class="sxs-lookup"><span data-stu-id="d7674-184">Alter the main thread by setting the client thread to STA or MTA.</span></span> <span data-ttu-id="d7674-185">たとえば、C# クライアントが多くの STA COM コンポーネントを呼び出す場合には、メイン スレッドを STA に設定してアパートメント間のマーシャリングを回避できます。</span><span class="sxs-lookup"><span data-stu-id="d7674-185">For example, if your C# client calls many STA COM components, you can avoid cross-apartment marshaling by setting the main thread to STA.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7674-186">C# クライアントのスレッドを STA に設定すると、MTA COM コンポーネントへの呼び出しにはアパートメント間のマーシャリングが必要となります。</span><span class="sxs-lookup"><span data-stu-id="d7674-186">Once the thread of a C# client is set to STA, calls to MTA COM components will require cross-apartment marshaling.</span></span>  
  
 <span data-ttu-id="d7674-187">アパートメント モデルを明示的に選択する方法については、「[マネージとアンマネージ スレッド](http://msdn.microsoft.com/en-us/db425c20-4b2f-4433-bf96-76071c7881e5)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7674-187">For instructions on explicitly selecting an apartment model, see [Managed and Unmanaged Threading](http://msdn.microsoft.com/en-us/db425c20-4b2f-4433-bf96-76071c7881e5).</span></span>  
  
 [<span data-ttu-id="d7674-188">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="d7674-188">Back to top</span></span>](#top)  
  
<a name="marshaling_remote_calls"></a>   
## <a name="marshaling-remote-calls"></a><span data-ttu-id="d7674-189">リモートの呼び出しのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="d7674-189">Marshaling Remote Calls</span></span>  
 <span data-ttu-id="d7674-190">アパートメント間のマーシャリングの場合と同様に、COM マーシャリングは、オブジェクトが別個のプロセス内に存在するときには常に、マネージ コードとアンマネージ コード間の各呼び出しに関与します。</span><span class="sxs-lookup"><span data-stu-id="d7674-190">As with cross-apartment marshaling, COM marshaling is involved in each call between managed and unmanaged code whenever the objects reside in separate processes.</span></span> <span data-ttu-id="d7674-191">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d7674-191">For example:</span></span>  
  
-   <span data-ttu-id="d7674-192">リモート ホスト上のマネージ サーバーを呼び出す COM クライアントは、分散 COM (DCOM) を使用します。</span><span class="sxs-lookup"><span data-stu-id="d7674-192">A COM client that invokes a managed server on a remote host uses distributed COM (DCOM).</span></span>  
  
-   <span data-ttu-id="d7674-193">リモート ホスト上の COM サーバーを呼び出すマネージ クライアントは、DCOM を使用します。</span><span class="sxs-lookup"><span data-stu-id="d7674-193">A managed client that invokes a COM server on a remote host uses DCOM.</span></span>  
  
 <span data-ttu-id="d7674-194">次の図は、相互運用マーシャリングと COM マーシャリングが、プロセスとホストの境界を越えて通信チャネルを提供する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d7674-194">The following illustration shows how interop marshaling and COM marshaling provide communications channels across process and host boundaries.</span></span>  
  
 <span data-ttu-id="d7674-195">![COM マーシャリング](../../../docs/framework/interop/media/interophost.gif "interophost")</span><span class="sxs-lookup"><span data-stu-id="d7674-195">![COM marshaling](../../../docs/framework/interop/media/interophost.gif "interophost")</span></span>  
<span data-ttu-id="d7674-196">プロセス間のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="d7674-196">Cross-process marshaling</span></span>  
  
### <a name="preserving-identity"></a><span data-ttu-id="d7674-197">ID の保持</span><span class="sxs-lookup"><span data-stu-id="d7674-197">Preserving Identity</span></span>  
 <span data-ttu-id="d7674-198">共通言語ランタイムは、マネージ参照とアンマネージ参照の ID を保持します。</span><span class="sxs-lookup"><span data-stu-id="d7674-198">The common language runtime preserves the identity of managed and unmanaged references.</span></span> <span data-ttu-id="d7674-199">次の図は、プロセスとホストの境界を越えている、直接アンマネージ参照 (上の行) と直接マネージ参照 (下の行) のフローを示しています。</span><span class="sxs-lookup"><span data-stu-id="d7674-199">The following illustration shows the flow of direct unmanaged references (top row) and direct managed references (bottom row) across process and host boundaries.</span></span>  
  
 <span data-ttu-id="d7674-200">![COM 呼び出し可能ラッパーとランタイム呼び出し可能ラッパー](../../../docs/framework/interop/media/interopdirectref.gif "interopdirectref")</span><span class="sxs-lookup"><span data-stu-id="d7674-200">![COM callable wrapper and runtime callable wrapper](../../../docs/framework/interop/media/interopdirectref.gif "interopdirectref")</span></span>  
<span data-ttu-id="d7674-201">プロセスとホストの境界を越えて渡される参照</span><span class="sxs-lookup"><span data-stu-id="d7674-201">Reference passing across process and host boundaries</span></span>  
  
 <span data-ttu-id="d7674-202">この図では:</span><span class="sxs-lookup"><span data-stu-id="d7674-202">In this illustration:</span></span>  
  
-   <span data-ttu-id="d7674-203">アンマネージ クライアントは、COM オブジェクトへの参照を、リモート ホストからその参照を取得するマネージ オブジェクトから取得します。</span><span class="sxs-lookup"><span data-stu-id="d7674-203">An unmanaged client gets a reference to a COM object from a managed object that gets this reference from a remote host.</span></span> <span data-ttu-id="d7674-204">リモート処理のメカニズムは DCOM です。</span><span class="sxs-lookup"><span data-stu-id="d7674-204">The remoting mechanism is DCOM.</span></span>  
  
-   <span data-ttu-id="d7674-205">マネージ クライアントは、マネージ オブジェクトへの参照を、リモート ホストからその参照を取得している COM オブジェクトから取得します。</span><span class="sxs-lookup"><span data-stu-id="d7674-205">A managed client gets a reference to a managed object from a COM object that gets this reference from a remote host.</span></span> <span data-ttu-id="d7674-206">リモート処理のメカニズムは DCOM です。</span><span class="sxs-lookup"><span data-stu-id="d7674-206">The remoting mechanism is DCOM.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7674-207">マネージ サーバーのエクスポート済みタイプ ライブラリを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7674-207">The exported type library of the managed server must be registered.</span></span>  
  
 <span data-ttu-id="d7674-208">呼び出し元と呼び出し先の間のプロセス境界の数は関連していません。同じ直接参照が、イン プロセスおよびアウト プロセスの呼び出しで発生します。</span><span class="sxs-lookup"><span data-stu-id="d7674-208">The number of process boundaries between caller and callee is irrelevant; the same direct referencing occurs for in-process and out-of-process calls.</span></span>  
  
### <a name="managed-remoting"></a><span data-ttu-id="d7674-209">マネージ リモート処理</span><span class="sxs-lookup"><span data-stu-id="d7674-209">Managed Remoting</span></span>  
 <span data-ttu-id="d7674-210">ランタイムは、プロセスとホストの境界を越えてマネージ オブジェクト間に通信チャネルを確立するために使用できる、マネージ リモート処理も提供します。</span><span class="sxs-lookup"><span data-stu-id="d7674-210">The runtime also provides managed remoting, which you can use to establish a communications channel between managed objects across process and host boundaries.</span></span> <span data-ttu-id="d7674-211">次の図に示すように、マネージ リモート処理は、通信コンポーネントの間のファイアウォールに対応できます。</span><span class="sxs-lookup"><span data-stu-id="d7674-211">Managed remoting can accommodate a firewall between the communicating components, as the following illustration shows.</span></span>  
  
 <span data-ttu-id="d7674-212">![SOAP または TcpChannel](../../../docs/framework/interop/media/interopremotesoap.gif "interopremotesoap")</span><span class="sxs-lookup"><span data-stu-id="d7674-212">![SOAP or TcpChannel](../../../docs/framework/interop/media/interopremotesoap.gif "interopremotesoap")</span></span>  
<span data-ttu-id="d7674-213">SOAP または TcpChannel クラスを使用するファイアウォールを越えたリモート呼び出し</span><span class="sxs-lookup"><span data-stu-id="d7674-213">Remote calls across firewalls using SOAP or the TcpChannel class</span></span>  
  
 <span data-ttu-id="d7674-214">[サービス コンポーネント](http://msdn.microsoft.com/en-us/f109ee24-81ad-4d99-9892-51ac6f34978c)と COM の間の呼び出しなど、一部のアンマネージ呼び出しは SOAP を介して伝達できます。</span><span class="sxs-lookup"><span data-stu-id="d7674-214">Some unmanaged calls can be channeled through SOAP, such as the calls between [serviced components](http://msdn.microsoft.com/en-us/f109ee24-81ad-4d99-9892-51ac6f34978c) and COM.</span></span>  
  
 [<span data-ttu-id="d7674-215">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="d7674-215">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="d7674-216">関連トピック</span><span class="sxs-lookup"><span data-stu-id="d7674-216">Related Topics</span></span>  
  
|<span data-ttu-id="d7674-217">タイトル</span><span class="sxs-lookup"><span data-stu-id="d7674-217">Title</span></span>|<span data-ttu-id="d7674-218">説明</span><span class="sxs-lookup"><span data-stu-id="d7674-218">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d7674-219">既定のマーシャリング動作</span><span class="sxs-lookup"><span data-stu-id="d7674-219">Default Marshaling Behavior</span></span>](../../../docs/framework/interop/default-marshaling-behavior.md)|<span data-ttu-id="d7674-220">相互運用マーシャリング サービスがデータのマーシャリングに使用する規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7674-220">Describes the rules that the interop marshaling service uses to marshal data.</span></span>|  
|[<span data-ttu-id="d7674-221">プラットフォーム呼び出しによるデータのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="d7674-221">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)|<span data-ttu-id="d7674-222">メソッドのパラメーターを宣言してアンマネージ ライブラリによってエクスポートされた関数に引数を渡す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7674-222">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>|  
|[<span data-ttu-id="d7674-223">COM 相互運用機能によるデータのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="d7674-223">Marshaling Data with COM Interop</span></span>](../../../docs/framework/interop/marshaling-data-with-com-interop.md)|<span data-ttu-id="d7674-224">COM ラッパーをカスタマイズしてマーシャリング動作を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7674-224">Describes how to customize COM wrappers to alter marshaling behavior.</span></span>|  
|[<span data-ttu-id="d7674-225">方法: マネージ コード DCOM を WCF に移行する</span><span class="sxs-lookup"><span data-stu-id="d7674-225">How to: Migrate Managed-Code DCOM to WCF</span></span>](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)|<span data-ttu-id="d7674-226">DCOM から WCF に移行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7674-226">Describes how to migrate from DCOM to WCF.</span></span>|  
|[<span data-ttu-id="d7674-227">方法: HRESULT に例外を割り当てる</span><span class="sxs-lookup"><span data-stu-id="d7674-227">How to: Map HRESULTs and Exceptions</span></span>](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)|<span data-ttu-id="d7674-228">HRESULT にカスタム例外をマップする方法について説明し、各 HRESULT から .NET Framework での同等の例外クラスへの完全なマッピングを示します。</span><span class="sxs-lookup"><span data-stu-id="d7674-228">Describes how to map custom exceptions to HRESULTs and provides the complete mapping from each HRESULT to its comparable exception class in the .NET Framework.</span></span>|  
|[<span data-ttu-id="d7674-229">ジェネリック型を使用する相互運用</span><span class="sxs-lookup"><span data-stu-id="d7674-229">Interoperating Using Generic Types</span></span>](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)|<span data-ttu-id="d7674-230">COM 相互運用性のジェネリック型を使用するとき、どのアクションがサポートされるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d7674-230">Describes which actions are supported when using generic types for COM interoperability.</span></span>|  
|[<span data-ttu-id="d7674-231">アンマネージ コードとの相互運用</span><span class="sxs-lookup"><span data-stu-id="d7674-231">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)|<span data-ttu-id="d7674-232">共通言語ランタイムが提供する相互運用サービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d7674-232">Describes interoperability services provided by the common language runtime.</span></span>|  
|[<span data-ttu-id="d7674-233">高度な COM 相互運用性</span><span class="sxs-lookup"><span data-stu-id="d7674-233">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)|<span data-ttu-id="d7674-234">.NET Framework アプリケーションに COM コンポーネントを組み込む方法についての詳細情報へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="d7674-234">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>|  
|[<span data-ttu-id="d7674-235">相互運用のためのデザインの考慮事項</span><span class="sxs-lookup"><span data-stu-id="d7674-235">Design Considerations for Interoperation</span></span>](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)|<span data-ttu-id="d7674-236">統合 COM コンポーネントを記述するためのヒントを示します。</span><span class="sxs-lookup"><span data-stu-id="d7674-236">Provides tips for writing integrated COM components.</span></span>|  
  
 [<span data-ttu-id="d7674-237">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="d7674-237">Back to top</span></span>](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a><span data-ttu-id="d7674-238">参照</span><span class="sxs-lookup"><span data-stu-id="d7674-238">Reference</span></span>  
 <xref:System.Runtime.InteropServices?displayProperty=nameWithType>  
  
 [<span data-ttu-id="d7674-239">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="d7674-239">Back to top</span></span>](#top)
