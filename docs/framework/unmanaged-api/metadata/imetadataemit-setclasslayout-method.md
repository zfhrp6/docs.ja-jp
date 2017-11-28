---
title: "IMetaDataEmit::SetClassLayout メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a68d94cbea408bee90b117965f83f760ba7ea5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout メソッド
前回の呼び出しで定義されているクラスのフィールドのレイアウトが完了した[DefineTypeDef メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `td`  
 [in]`mdTypeDef`レイアウトされるクラスを指定するトークン。  
  
 `dwPackSize`  
 [in]パッキング サイズ: 1、2、4、8 バイトまたは 16 バイトです。 パッキング サイズは、横にあるフィールド間のバイト数です。  
  
 `rFieldOffsets`  
 [in]配列[COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)構造体、クラスのフィールドとフィールドのクラス内でオフセットをそれぞれ指定します。 配列を終了`mdTokenNil`です。  
  
 `ulClassSize`  
 [in]クラスのバイト単位のサイズ。  
  
## <a name="remarks"></a>コメント  
 クラスが最初に呼び出すことによって定義されている、 [imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)メソッド、およびクラスのフィールドについて次の 3 つのレイアウトのいずれかを指定する: 自動、シーケンシャル、または明示的なです。 通常は自動レイアウトを使用してランタイムにフィールドをレイアウトする最善の方法を選択します。  
  
 ただし、フィールドをアンマネージ コードが使用する配置に従ってレイアウトが必要な場合があります。 この例では、シーケンシャルまたは明示的なレイアウトと呼び出しを選択して`SetClassLayout`フィールドのレイアウトを完了します。  
  
-   シーケンシャル レイアウト: パッキング サイズを指定します。 フィールドは、自然なサイズ、またはどの結果フィールドのオフセットは小さく、パッキング サイズに従って配置します。 設定`rFieldOffsets`と`ulClassSize`をゼロにします。  
  
-   明示的なレイアウト: 各フィールドのオフセットを指定するか、クラスのサイズおよびパッキング サイズを指定します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
