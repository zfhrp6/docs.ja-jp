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
ms.openlocfilehash: 35f3c00f3a0efd41c425ba29f8465a73e78d624c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="d2230-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="d2230-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="d2230-103">同じリストを反復処理するため、現在の列挙子と同じ状態の別の未加工入力デバイスの列挙子を作成します。</span><span class="sxs-lookup"><span data-stu-id="d2230-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2230-104">構文</span><span class="sxs-lookup"><span data-stu-id="d2230-104">Syntax</span></span>  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2230-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d2230-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="d2230-106">[out]受け取る出力変数のアドレス、 [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md)インターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="d2230-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="d2230-107">メソッドが成功した場合は、この output 変数の値は定義されません。</span><span class="sxs-lookup"><span data-stu-id="d2230-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="d2230-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="d2230-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="d2230-109">HRESULT: このメソッドは、E_INVALIDARG、E_UNEXPECTED、E_OUTOFMEMORY は、標準の戻り値をサポートします。</span><span class="sxs-lookup"><span data-stu-id="d2230-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2230-110">コメント</span><span class="sxs-lookup"><span data-stu-id="d2230-110">Remarks</span></span>  
 <span data-ttu-id="d2230-111">このメソッドでは、後でそのポイントを返すために、列挙のシーケンスで、ポイントを録音することです。</span><span class="sxs-lookup"><span data-stu-id="d2230-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="d2230-112">呼び出し元は、最初の列挙子から個別に新しいこの列挙子を解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2230-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
