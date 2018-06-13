---
title: ISymUnmanagedDocument::GetLanguageVendor メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguageVendor
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguageVendor
helpviewer_keywords:
- GetLanguageVendor method [.NET Framework debugging]
- ISymUnmanagedDocument::GetLanguageVendor method [.NET Framework debugging]
ms.assetid: 1d4b702e-4922-441d-8b44-03804284f70b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a6830f47d5cac2cf9c84144c18486489b0ec581
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424532"
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a>ISymUnmanagedDocument::GetLanguageVendor メソッド
このドキュメントの言語の販売元を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]言語の販売元を受け取る変数へのポインター。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK です。  
  
## <a name="see-also"></a>関連項目  
 [ISymUnmanagedDocument インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
