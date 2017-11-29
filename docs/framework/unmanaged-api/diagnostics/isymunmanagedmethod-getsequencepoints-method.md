---
title: "ISymUnmanagedMethod::GetSequencePoints メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetSequencePoints
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3cde9de634534acdeafa40bd7a94c46624e49604
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints メソッド
このメソッド内のすべてのシーケンス ポイントを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cPoints`  
 [in]A`ULONG32`のサイズを受け取る、 `offsets`、 `documents`、 `lines`、 `columns`、 `endLines`、および`endColumns`配列。  
  
 `pcPoints`  
 [out]ポインター、`ULONG32`シーケンス ポイントの格納に必要なバッファーの長さを受け取る。  
  
 `offsets`  
 [in]シーケンス ポイントのメソッドの先頭から language (MSIL) オフセットを中級者向けの Microsoft を格納する配列。  
  
 `documents`  
 [in]シーケンス ポイントが存在するドキュメントを格納する配列。  
  
 `lines`  
 [in]シーケンス ポイントが存在するドキュメントの行を格納する配列。  
  
 `columns`  
 [in]シーケンス ポイントが存在するドキュメント内の列を格納する配列。  
  
 `endLines`  
 [in]シーケンス ポイントが終了するドキュメント内の行の配列。  
  
 `endColumns`  
 [in]シーケンス ポイントが終了するドキュメント内の列の配列。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>関連項目  
 [ISymUnmanagedMethod インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
