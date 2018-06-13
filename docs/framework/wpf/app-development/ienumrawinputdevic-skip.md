---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: b03d141f1d2bfc18428c2f8651a340b789cfb995
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548556"
---
# <a name="ienumrawinputdevicskip"></a><span data-ttu-id="f2a42-102">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="f2a42-102">IEnumRAWINPUTDEVIC:Skip</span></span>
<span data-ttu-id="f2a42-103">列挙子は、[次へ] をスキップするように指示`celt`列挙体の要素を次の呼び出しに[IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)それらの要素は返されません。</span><span class="sxs-lookup"><span data-stu-id="f2a42-103">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) will not return those elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2a42-104">構文</span><span class="sxs-lookup"><span data-stu-id="f2a42-104">Syntax</span></span>  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2a42-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f2a42-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="f2a42-106">[in]スキップする要素の数。</span><span class="sxs-lookup"><span data-stu-id="f2a42-106">[in] Number of elements to be skipped.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="f2a42-107">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="f2a42-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="f2a42-108">指定された要素の数が `celt` の場合は HRESULT: S_OK。それ以外の場合は S_FALSE。</span><span class="sxs-lookup"><span data-stu-id="f2a42-108">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
