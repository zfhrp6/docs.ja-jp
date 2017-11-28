---
title: "ISymUnmanagedWriter::Initialize メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bae368919941e6a0b234736f789320b62405a17b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterinitialize-method"></a>ISymUnmanagedWriter::Initialize メソッド
このライターが関連付けられるメタデータ エミッタ インターフェイスを設定し、デバッグ シンボルが書き込まれる出力ファイル名を設定します。  
  
 このメソッドを 1 回だけ呼び出すことができるし、その他のライター メソッドより前に呼び出す必要があります。 一部の開発者は、ファイル名を必要があります。 ただし、ファイル名には、ファイル名を使用しないライターへの悪影響を及ぼすことがなく、このメソッドに常に渡すことができます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `emitter`  
 [in]メタデータ エミッタ インターフェイスへのポインター。  
  
 `filename`  
 [in]デバッグ シンボルの書き込み先となるファイル名。 ファイル名を使用しないライターに対してファイル名を指定した場合、このパラメーターは無視されます。  
  
 `pIStream`  
 [in]シンボルのライターにシンボルを出力、指定した場合、指定された<xref:System.Runtime.InteropServices.ComTypes.IStream>で指定されたファイルにではなく、`filename`パラメーター。 
          `pIStream` パラメーターは省略可能です。  
  
 `fFullBuild`  
 [in]`true`場合、これは、完全な再構築`false`インクリメンタル コンパイルの場合。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>関連項目  
 [ISymUnmanagedWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Initialize2 メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
