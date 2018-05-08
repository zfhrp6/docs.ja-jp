---
title: ISymUnmanagedMethod::GetOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d88e9279f70c36fd8a9c626972e33305cded5fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedmethodgetoffset-method"></a>ISymUnmanagedMethod::GetOffset メソッド
ドキュメント内の指定位置に対応するこのメソッド内のオフセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `document`  
 [in]オフセットを要求する対象のドキュメントへのポインター。  
  
 `line`  
 [in]オフセットの要求対象となるドキュメント行。  
  
 `column`  
 [in]オフセットの要求対象となるドキュメント列。  
  
 `pRetVal`  
 [out]ポインター、`ULONG32`オフセットを受け取る。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>関連項目  
 [ISymUnmanagedMethod インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
