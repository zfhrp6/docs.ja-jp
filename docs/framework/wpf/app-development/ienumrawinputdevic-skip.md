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
# <a name="ienumrawinputdevicskip"></a>IEnumRAWINPUTDEVIC:Skip
列挙子は、[次へ] をスキップするように指示`celt`列挙体の要素を次の呼び出しに[IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)それらの要素は返されません。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
  
 [in]スキップする要素の数。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 指定された要素の数が `celt` の場合は HRESULT: S_OK。それ以外の場合は S_FALSE。
