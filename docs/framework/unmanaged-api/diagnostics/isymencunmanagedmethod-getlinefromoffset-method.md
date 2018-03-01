---
title: "ISymENCUnmanagedMethod::GetLineFromOffset メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 535c0310a3220c5691f26c9081f6d2f747196e91
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset メソッド
オフセットに関連付けられている行の情報を取得します。 場合オフセット パラメーター (`dwOffset`) は、シーケンス ポイントでは、このメソッドは、前のオフセットに関連付けられている行の情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwOffset`  
 [in]A`ULONG32`オフセットを格納しています。  
  
 `pline`  
 [out]ポインター、`ULONG32`行を受け取る。  
  
 `pcolumn`  
 [out]ポインター、`ULONG32`列を受け取る。  
  
 `pendLine`  
 [out]ポインター、`ULONG32`の最終行を受け取る。  
  
 `pendColumn`  
 [out]ポインター、`ULONG32`を受け取る最終列。  
  
 `pdwStartOffset`  
 [out]ポインター、`ULONG32`関連付けられたシーケンス ポイントを受け取る。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>参照  
 [ISymENCUnmanagedMethod インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
