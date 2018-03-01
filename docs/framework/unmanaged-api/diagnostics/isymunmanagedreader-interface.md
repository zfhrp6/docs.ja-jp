---
title: "ISymUnmanagedReader インターフェイス"
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
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e8daea11292cb37deb8e956e6a666c14579fbfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader インターフェイス
ドキュメント、メソッド、およびシンボル ストア内の変数へのアクセスを提供するシンボル リーダーを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetDocument メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|ドキュメントを検索します。|  
|[GetDocuments メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|シンボル ストアで定義されているすべてのドキュメントの配列を返します。|  
|[GetDocumentVersion メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|指定されたドキュメントの指定されたバージョンを取得します。|  
|[GetGlobalVariables メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|すべてのグローバル変数を返します。|  
|[GetMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|メソッドのトークンを指定、シンボル リーダー メソッドを取得します。|  
|[GetMethodByVersion メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|メソッドのトークンと編集、コピーのバージョン番号を指定、シンボル リーダー メソッドを取得します。|  
|[GetMethodFromDocumentPosition メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|ドキュメント内の指定位置にブレークポイントを含むメソッドを返します。|  
|[GetMethodsFromDocumentPosition メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|メソッドのドキュメントで指定された位置にブレークポイントを含むそれぞれの配列を返します。|  
|[GetMethodVersion メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|メソッドのバージョンを取得します。|  
|[GetNamespaces メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|このシンボル ストア内のグローバル スコープで定義された名前空間を取得します。|  
|[GetSymAttribute メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|その名前に基づくカスタム属性を取得します。|  
|[GetSymbolStoreFileName メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|シンボル ストアのディスク上のファイル名を提供します。|  
|[GetUserEntryPoint メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|存在する場合は、モジュールのユーザー エントリ ポイントとして指定されたメソッドを返します。|  
|[GetVariables メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|親と名前を指定された非ローカル変数を返します。|  
|[Initialize メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|このリーダーは、モジュールのファイル名と共に、関連付けられるメタデータ インポーターのインターフェイスで、シンボル リーダーを初期化します。|  
|[ReplaceSymbolStore メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|既存のシンボル ストアをデルタ シンボル ストアで置き換えます。|  
|[UpdateSymbolStore メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|既存のシンボル ストアをデルタ シンボル ストアで更新します。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>参照  
 [シンボル ストア診断インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedReader2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
