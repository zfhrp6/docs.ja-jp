---
title: ISymUnmanagedMethod インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 728acc09f739fe567fca4a2571cbabf1ba8838a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427432"
---
# <a name="isymunmanagedmethod-interface"></a>ISymUnmanagedMethod インターフェイス
シンボル ストア内のメソッドを表します。 このインターフェイスは、型に関連する属性ではなく、メソッドの symbol 関連の属性のみへのアクセスを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetNamespace メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|このメソッドが定義されている外側の名前空間を取得します。|  
|[GetOffset メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|ドキュメント内の指定位置に対応するこのメソッド内のオフセットを返します。|  
|[GetParameters メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|このメソッドのパラメーターを取得します。|  
|[GetRanges メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|指定されたドキュメント内の位置には、Microsoft intermediate language (MSIL をこのメソッド内に含まれる位置) の範囲に先頭と末尾オフセットのペアの対応する配列を返します。|  
|[GetRootScope メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|このメソッド内でルート構文スコープを取得します。 このスコープはメソッド全体を囲みます。|  
|[GetScopeFromOffSet メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|このメソッドを指定したオフセットを囲む内で最も外側の構文のスコープを取得します。|  
|[GetSequencePointCount メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|このメソッド内のシーケンス ポイントの数を取得します。|  
|[GetSequencePoints メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|このメソッド内のすべてのシーケンス ポイントを取得します。|  
|[GetSourceStartEnd メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|このメソッドのソースの開始と終了のドキュメントの位置を取得します。|  
|[GetToken メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|このメソッドのメタデータ トークンを返します。|  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>関連項目  
 [シンボル ストア診断インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
