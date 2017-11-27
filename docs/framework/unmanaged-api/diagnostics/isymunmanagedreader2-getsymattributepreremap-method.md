---
title: "ISymUnmanagedReader2::GetSymAttributePreRemap メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2.GetSymAttributePreRemap
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 75608d89b6fd34570166718de824150b0621c84e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a>ISymUnmanagedReader2::GetSymAttributePreRemap メソッド
その名前に基づくカスタム属性を取得します。 メタデータのカスタム属性とは異なり、これらの属性は、シンボル ストアに保持されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `parent`  
 [in]親のメタデータ トークンです。  
  
 `name`  
 [in]ポインター、`WCHAR`名前を格納しています。  
  
 `cBuffer`  
 [in]A`ULONG32`のサイズを示す、`buffer`配列。  
  
 `pcBuffer`  
 [out]ポインター、`ULONG32`属性データの格納に必要なバッファーのサイズを受け取る。  
  
 `buffer`  
 [out]属性データを受け取るバッファーへのポインター。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>関連項目  
 [ISymUnmanagedReader2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
