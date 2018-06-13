---
title: IMetaDataEmit::GetSaveSize メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d9a65f76aed00e2b848f8603f1fee4d6acc91f99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449158"
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize メソッド
現在のスコープ内には、バイナリの推定サイズ アセンブリとそのメタデータを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `fSave`  
 [in]値、 [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md)正確またはおおよそのサイズを取得するかどうかを指定する列挙です。 有効な値は 3 つだけ: cssAccurate、cssQuick、および cssDiscardTransientCAs:  
  
-   cssAccurate では、正確な保存のサイズを返しますが、計算に時間がかかります。  
  
-   cssQuick は安全性、用に埋め込まれて、サイズを返しますが、計算時間がかかりません。  
  
-   cssDiscardTransientCAs 指示`GetSaveSize`ことができますを破棄破棄できるカスタム属性です。  
  
 `pdwSaveSize`  
 [out]ファイルを保存するために必要なサイズへのポインター。  
  
## <a name="remarks"></a>コメント  
 `GetSaveSize` 必要に応じて、(バイト単位) を現在のスコープ内のアセンブリとそのすべてのメタデータを保存する領域を計算します。 (への呼び出し、 [imetadataemit::savetostream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)メソッドはこのバイト数を出力します)。  
  
 呼び出し元が実装されている場合、 [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)インターフェイス (を通じて[imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)または[imetadataemit::merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md))、`GetSaveSize`は 2 つのパスを実行最適化し、それを圧縮するメタデータ。 それ以外の場合、最適化は行われません。  
  
 最適化を実行すると、最初のパスは単にインポート時の検索のパフォーマンスを調整するメタデータ構造体を並べ替えます。 この手順は、通常、レコードが移動、今後の参照用のツールで保持されるトークンが無効にした、副作用とで発生します。 メタデータに通知しませんまでこれらのトークンの変更の呼び出し元は、2 番目のパスの後にただしです。 2 番目のパスでは、さまざまな最適化が実行退席中の (事前バインディング) の最適化などのメタデータの全体的なサイズの削減を意図した`mdTypeRef`と`mdMemberRef`トークンの参照先が型またはメンバーで宣言されているときに、現在のメタデータ スコープ。 このパスでは、トークンのマッピングの別のラウンドが発生します。 このパスの後はメタデータ エンジンに通知、呼び出し元からその`IMapToken`のいずれかのインターフェイスは、トークンの値を変更します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
