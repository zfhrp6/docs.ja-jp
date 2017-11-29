---
title: "ISymUnmanagedReader::Initialize メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5917fbe3cebe9b1e9ab91d113aee2461f414c14d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize メソッド
このリーダーは、モジュールのファイル名と共に、関連付けられるメタデータ インポーターのインターフェイスで、シンボル リーダーを初期化します。  
  
> [!NOTE]
>  このメソッドは、1 回だけ呼び出すことができ、その他のリーダー メソッドより前に呼び出す必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `importer`  
 [in]このリーダーが関連付けられるメタデータ インポーターのインターフェイスです。  
  
 `filename`  
 [in]モジュールのファイル名。 使用することができます、`pIStream`パラメーター代わりにします。  
  
 `searchPath`  
 [in]検索するパス。 このパラメーターは省略できます。  
  
 `pIStream`  
 [in]Filename パラメーターの代わりとして使用するファイル ストリーム。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="remarks"></a>コメント  
 1 つだけを指定する必要があります、`filename`または`pIStream`パラメーターは、両方は使用できません。 
          `searchPath` パラメーターは省略可能です。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>関連項目  
 [ISymUnmanagedReader インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
