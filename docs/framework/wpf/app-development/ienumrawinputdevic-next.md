---
title: IEnumRAWINPUTDEVIC:Next
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 644a8e724a280a8b23048a381a099acd6e655d2c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="aa905-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="aa905-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="aa905-103">次の列挙`celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp)構造体、列挙子の一覧でそれらを返す`rgelt`列挙型の要素の実際の数と共に`pceltFetched`です。</span><span class="sxs-lookup"><span data-stu-id="aa905-103">Enumerates the next `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa905-104">構文</span><span class="sxs-lookup"><span data-stu-id="aa905-104">Syntax</span></span>  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa905-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa905-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="aa905-106">[in]数[RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp)構造体で返される`rgelt`です。</span><span class="sxs-lookup"><span data-stu-id="aa905-106">[in] Number of [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="aa905-107">[out] 列挙された RAWINPUTDEVICE 構造体を受け取る size celt (またはそれ以上) の配列。</span><span class="sxs-lookup"><span data-stu-id="aa905-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="aa905-108">[out] `rgelt` に実際に指定された要素の数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa905-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="aa905-109">`NULL` が 1 の場合、呼び出し元は `rgelt` に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="aa905-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="aa905-110">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="aa905-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="aa905-111">指定された要素の数が `celt` の場合は HRESULT: S_OK。それ以外の場合は S_FALSE。</span><span class="sxs-lookup"><span data-stu-id="aa905-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
