---
title: COM ラッパー
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60f5acf6ed8a7fe0bb2e6293666c33a479d25643
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="com-wrappers"></a><span data-ttu-id="1cc6f-102">COM ラッパー</span><span class="sxs-lookup"><span data-stu-id="1cc6f-102">COM Wrappers</span></span>
<span data-ttu-id="1cc6f-103">COM は、次のいくつかの重要な点で、.NET Framework オブジェクト モデルとは異なります。</span><span class="sxs-lookup"><span data-stu-id="1cc6f-103">COM differs from the .NET Framework object model in several important ways:</span></span>  
  
-   <span data-ttu-id="1cc6f-104">COM オブジェクトのクライアントは、COM オブジェクトの有効期間を管理する必要があります。共通言語ランタイムはその環境でのオブジェクトの有効期間を管理します。</span><span class="sxs-lookup"><span data-stu-id="1cc6f-104">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
-   <span data-ttu-id="1cc6f-105">COM オブジェクトのクライアントは、サービスを提供するインターフェイスを要求し、インターフェイス ポインターを取得して、そのサービスが利用可能かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="1cc6f-105">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="1cc6f-106">.NET オブジェクトのクライアントは、リフレクションを使用してオブジェクトの機能の説明を取得できます。</span><span class="sxs-lookup"><span data-stu-id="1cc6f-106">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
-   <span data-ttu-id="1cc6f-107">NET オブジェクトは、.NET Framework の実行環境によって管理されるメモリ内に存在します。</span><span class="sxs-lookup"><span data-stu-id="1cc6f-107">NET objects reside in memory managed by the .NET Framework execution environment.</span></span> <span data-ttu-id="1cc6f-108">実行環境では、パフォーマンス上の理由からオブジェクトをメモリ内で移動させることができ、移動先のオブジェクトへのすべての参照を更新できます。</span><span class="sxs-lookup"><span data-stu-id="1cc6f-108">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="1cc6f-109">オブジェクトへのポインターを取得するアンマネージ クライアントは、そのオブジェクトに依存するので同じ場所にとどまります。</span><span class="sxs-lookup"><span data-stu-id="1cc6f-109">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="1cc6f-110">これらのクライアントには、場所が固定されていないオブジェクトを処理するための機構がありません。</span><span class="sxs-lookup"><span data-stu-id="1cc6f-110">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="1cc6f-111">このような相違を克服するために、ランタイムはラッパー クラスを提供して、マネージ クライアントとアンマネージ クライアントの両方がそれぞれの環境内でオブジェクトを呼び出していると認識するようにします。</span><span class="sxs-lookup"><span data-stu-id="1cc6f-111">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="1cc6f-112">マネージ クライアントが COM オブジェクトでメソッドを呼び出すたびに、ランタイムは[ランタイム呼び出し可能ラッパー](runtime-callable-wrapper.md) (RCW) を作成します。</span><span class="sxs-lookup"><span data-stu-id="1cc6f-112">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="1cc6f-113">RCW は、特にマネージ参照機構とアンマネージ参照機構の相違を抽象化します。</span><span class="sxs-lookup"><span data-stu-id="1cc6f-113">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="1cc6f-114">また、ランタイムは [COM 呼び出し可能ラッパー](com-callable-wrapper.md) (CCW) を作成して、プロセスを反転させ、COM クライアントがシームレスに .NET オブジェクトでメソッドを呼び出せるようにします。</span><span class="sxs-lookup"><span data-stu-id="1cc6f-114">The runtime also creates a [COM callable wrapper](com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="1cc6f-115">呼び出し元のコードと、ランタイムが作成するラッパー クラスの関係を示す図を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="1cc6f-115">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 <span data-ttu-id="1cc6f-116">![COM ラッパーの概要](media/bidirectional.gif "bidirectional")</span><span class="sxs-lookup"><span data-stu-id="1cc6f-116">![COM wrapper overview](media/bidirectional.gif "bidirectional")</span></span>  
<span data-ttu-id="1cc6f-117">COM ラッパーの概要</span><span class="sxs-lookup"><span data-stu-id="1cc6f-117">COM wrapper overview</span></span>  
  
 <span data-ttu-id="1cc6f-118">ほとんどの場合、ランタイムによって生成される標準の RCW または CCW は、COM と .NET Framework の境界をまたがる呼び出しに対して適切なマーシャリングを提供します。</span><span class="sxs-lookup"><span data-stu-id="1cc6f-118">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET Framework.</span></span> <span data-ttu-id="1cc6f-119">カスタム属性を使用することにより、必要に応じて、ランタイムがマネージ コードおよびアンマネージ コードを表わす方法を調整できます。</span><span class="sxs-lookup"><span data-stu-id="1cc6f-119">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc6f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="1cc6f-120">See Also</span></span>  
 <span data-ttu-id="1cc6f-121">[高度な COM 相互運用性](https://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1cc6f-121">[Advanced COM Interoperability](https://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb(v=vs.100))</span></span>  
 [<span data-ttu-id="1cc6f-122">ランタイム呼び出し可能ラッパー</span><span class="sxs-lookup"><span data-stu-id="1cc6f-122">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)  
 [<span data-ttu-id="1cc6f-123">COM 呼び出し可能ラッパー</span><span class="sxs-lookup"><span data-stu-id="1cc6f-123">COM Callable Wrapper</span></span>](com-callable-wrapper.md)  
 <span data-ttu-id="1cc6f-124">[標準ラッパーのカスタマイズ](https://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1cc6f-124">[Customizing Standard Wrappers](https://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d(v=vs.100))</span></span>  
 <span data-ttu-id="1cc6f-125">[方法 : ランタイム呼び出し可能ラッパーをカスタマイズする](https://msdn.microsoft.com/library/4a4bb3da-4d60-4517-99f2-78d46a681732(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1cc6f-125">[How to: Customize Runtime Callable Wrappers](https://msdn.microsoft.com/library/4a4bb3da-4d60-4517-99f2-78d46a681732(v=vs.100))</span></span>
