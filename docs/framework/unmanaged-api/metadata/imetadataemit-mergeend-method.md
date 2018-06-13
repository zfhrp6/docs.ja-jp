---
title: IMetaDataEmit::MergeEnd メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b794a62a0ac0d253f1431be29b43101816dc7233
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449443"
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd メソッド
現在のマージのスコープを 1 つまたは複数の以前の呼び出しで指定されたすべてのメタデータ スコープ[imetadataemit::merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT MergeEnd ();  
```  
  
#### <a name="parameters"></a>パラメーター  
 このメソッドには、パラメーターはありません。  
  
## <a name="remarks"></a>コメント  
 このルーチンは、メタデータの実際のマージをトリガー、すべてのインポート前に呼び出しを追加して指定した範囲`IMetaDataEmit::Merge`、現在の出力のスコープにします。  
  
 次の特殊な条件は、マージに適用されます。  
  
-   モジュールのバージョン id (MVID) インポートされることは、インポートのスコープ内のメタデータを一意になっているためです。  
  
-   既存のモジュール全体のプロパティは上書きされません。  
  
     モジュールのプロパティが既に設定されている現在のスコープのモジュールのプロパティはインポートされません。 ただし、現在のスコープでこのモジュールのプロパティが設定されていない場合、最初に検出された、1 回だけがインポートされます。 これらのモジュールのプロパティが再度発生する場合、重複しています。 (MVID) を除くすべてのモジュールのプロパティの値を比較し、重複部分が見つからない、エラーが発生します。  
  
-   型の定義 (`TypeDef`)、現在のスコープに重複がマージされません。 `TypeDef` オブジェクトはそれぞれに対して重複をチェック*オブジェクトの完全修飾名* + *GUID* + *バージョン番号*です。 名前または GUID のいずれかに一致があるその他の 2 つの要素のいずれかが異なる場合は、エラーが発生します。 それ以外の場合、3 つの項目をすべて一致する場合、`MergeEnd`エントリが重複しないことを確認するにはない場合、エラーが発生します。 この簡単なチェックを探します。  
  
    -   同じメンバー宣言と同じ順序で発生しています。 メンバーとしてフラグが付いている`mdPrivateScope`(を参照してください、 [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列挙型) です。 この確認に含まれていない特別にマージされます。  
  
    -   同じクラス レイアウトです。  
  
     つまり、`TypeDef`オブジェクト必要があります常に完全かつ一貫して定義するすべてのメタデータ スコープ内で宣言されている以外の完全定義があると見なされます (クラス) のメンバーの実装が複数のコンパイル単位に分散している場合すべてのスコープ内に存在しスコープごとにインクリメントは行われません。 たとえば、パラメーター名が、コントラクトに関連する場合は、する必要がありますに出力すると同じ方法すべてのスコープ関連する、ない場合、必要があるメタデータに対して出力されません。  
  
     例外は、`TypeDef`オブジェクトとしてフラグが設定された増分のメンバーを持つことができます`mdPrivateScope`です。 これらは、発生時に`MergeEnd`増分重複に関係なく、現在のスコープに追加します。 コンパイラは、プライベートのスコープを認識するため、コンパイラが規則を適用する行う必要があります。  
  
-   相対仮想アドレス (Rva) のインポートまたは; トピックとマージされていません。コンパイラは、この情報を再生成すると想定されます。  
  
-   アタッチされている項目がマージされた場合にのみ、カスタム属性がマージされます。 たとえば、クラスに関連付けられているカスタム属性は、クラスが最初に検出されたときにマージされます。 カスタム属性が関連付けられている場合、`TypeDef`または`MemberDef`(メンバー コンパイルのタイムスタンプ) などのコンパイル単位に固有であるはマージされませんおよび削除するか、このようなメタデータを更新するコンパイラの責任です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
