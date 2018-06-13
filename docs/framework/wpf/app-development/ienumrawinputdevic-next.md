---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: 3cf3231bd48290c5b6b0ce8eeb6534de564c0c85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546407"
---
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
次の列挙`celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp)構造体、列挙子の一覧でそれらを返す`rgelt`列挙型の要素の実際の数と共に`pceltFetched`です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
  
 [in]数[RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp)構造体で返される`rgelt`です。  
  
 `rgelt`  
  
 [out] 列挙された RAWINPUTDEVICE 構造体を受け取る size celt (またはそれ以上) の配列。  
  
 `pceltFetched`  
  
 [out] `rgelt` に実際に指定された要素の数へのポインター。 `NULL` が 1 の場合、呼び出し元は `rgelt` に渡すことができます。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 指定された要素の数が `celt` の場合は HRESULT: S_OK。それ以外の場合は S_FALSE。
