---
title: IEnumRAWINPUTDEVIC:Clone
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db218ec824dfe163946b0c1bd412efd0f78f4ad8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="7c357-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="7c357-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="7c357-103">同じリストを反復処理するため、現在の列挙子と同じ状態の別の未加工入力デバイスの列挙子を作成します。</span><span class="sxs-lookup"><span data-stu-id="7c357-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c357-104">構文</span><span class="sxs-lookup"><span data-stu-id="7c357-104">Syntax</span></span>  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c357-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7c357-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="7c357-106">[out]受け取る出力変数のアドレス、 [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md)インターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="7c357-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="7c357-107">メソッドが成功した場合は、この output 変数の値は定義されません。</span><span class="sxs-lookup"><span data-stu-id="7c357-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="7c357-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="7c357-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="7c357-109">HRESULT: このメソッドは、E_INVALIDARG、E_UNEXPECTED、E_OUTOFMEMORY は、標準の戻り値をサポートします。</span><span class="sxs-lookup"><span data-stu-id="7c357-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c357-110">コメント</span><span class="sxs-lookup"><span data-stu-id="7c357-110">Remarks</span></span>  
 <span data-ttu-id="7c357-111">このメソッドでは、後でそのポイントを返すために、列挙のシーケンスで、ポイントを録音することです。</span><span class="sxs-lookup"><span data-stu-id="7c357-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="7c357-112">呼び出し元は、最初の列挙子から個別に新しいこの列挙子を解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c357-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
