---
title: IEnumRAWINPUTDEVICE
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a93458e97ef317c425f3b51b1e3abc20ade2931b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="b1c32-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="b1c32-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="b1c32-103">このインターフェイスは、未加工入力デバイスを列挙し、 PresentationHost.exe でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="b1c32-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1c32-104">この API は、ローカル クライアント コンピューターでの使用のみを目的とし、サポートされています。</span><span class="sxs-lookup"><span data-stu-id="b1c32-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="b1c32-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="b1c32-105">Members</span></span>  
  
|<span data-ttu-id="b1c32-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b1c32-106">Member</span></span>|<span data-ttu-id="b1c32-107">説明</span><span class="sxs-lookup"><span data-stu-id="b1c32-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1c32-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="b1c32-108">IEnumRAWINPUTDEVIC:Next</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)|<span data-ttu-id="b1c32-109">次の `celt` 要素 (つまり RAWINPUTDEVICE 構造体) を、列挙子の一覧で列挙するとともに、それを `rgelt` で列挙された要素の実際の数とともに `pceltFetched` で返します。</span><span class="sxs-lookup"><span data-stu-id="b1c32-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="b1c32-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="b1c32-110">IEnumRAWINPUTDEVIC:Skip</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-skip.md)|<span data-ttu-id="b1c32-111">列挙子は、[次へ] をスキップするように指示`celt`列挙体の要素を次の呼び出しに[IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)それらの要素は返されません。</span><span class="sxs-lookup"><span data-stu-id="b1c32-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="b1c32-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="b1c32-112">IEnumRAWINPUTDEVIC:Reset</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-reset.md)|<span data-ttu-id="b1c32-113">列挙のシーケンスを最初にリセットします。</span><span class="sxs-lookup"><span data-stu-id="b1c32-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="b1c32-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="b1c32-114">IEnumRAWINPUTDEVIC:Clone</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-clone.md)|<span data-ttu-id="b1c32-115">同じリストを反復処理するため、現在の列挙子と同じ状態の別の未加工入力デバイスの列挙子を作成します。</span><span class="sxs-lookup"><span data-stu-id="b1c32-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1c32-116">参照</span><span class="sxs-lookup"><span data-stu-id="b1c32-116">See Also</span></span>  
 [<span data-ttu-id="b1c32-117">生の入力について</span><span class="sxs-lookup"><span data-stu-id="b1c32-117">About Raw Input</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/aboutrawinput.asp)
