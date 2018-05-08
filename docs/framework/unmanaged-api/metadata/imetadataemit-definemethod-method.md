---
title: IMetaDataEmit::DefineMethod メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53fd830cdefda58d40f96f8662a80d1888d963dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod メソッド
指定したシグネチャを持つメソッドまたはグローバル関数の定義を作成し、そのメソッドの定義にトークンを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineMethod (      
    [in]  mdTypeDef         td,   
    [in]  LPCWSTR           szName,   
    [in]  DWORD             dwMethodFlags,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [in]  ULONG             ulCodeRVA,   
    [in]  DWORD             dwImplFlags,   
    [out] mdMethodDef      *pmd  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `td`  
 [in]`mdTypedef`親クラスまたはメソッドの親インターフェイスのトークン。 設定`td`に`mdTokenNil`グローバル関数を定義している場合、します。  
  
 `szName`  
 [in]Unicode でメンバーの名前。  
  
 `dwMethodFlags`  
 [in]値、 [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)メソッドまたはグローバル関数の属性を指定する列挙体です。  
  
 `pvSigBlob`  
 [in]メソッドのシグネチャ。 提供された、署名が保持されます。 すべてのパラメーターの追加情報を指定する必要がある場合を使用して、 [imetadataemit::setparamprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)メソッドです。  
  
 `cbSigBlob`  
 [in]内のバイト数`pvSigBlob`です。  
  
 `ulCodeRVA`  
 [in]コードのアドレス。  
  
 `dwImplFlags`  
 [in]値、 [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)メソッドの実装の機能を指定する列挙です。  
  
 `pmd`  
 [out]メンバー トークンです。  
  
## <a name="remarks"></a>コメント  
 メタデータ API が、呼び出し元を出力に指定された外側のクラスまたはインターフェイスで指定されているのと同じ順序のメソッドを保持するには、`td`パラメーター。  
  
 使用に関する追加情報`DefineMethod`し、特定のパラメーターの設定のとおりです。  
  
## <a name="slots-in-the-v-table"></a>V テーブル内のスロット  
 ランタイムでは、メソッド定義を使用して、v-table スロットを設定します。 1 つまたは複数のスロットがスキップする必要がある場合、COM インターフェイスのレイアウトと同等の機能を保持する場合など、ダミー メソッドが定義されて v テーブル内のスロットを使用して設定、`dwMethodFlags`を`mdRTSpecialName`の値、 [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列挙として名前を指定します。  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>  
  
 ここで*SequenceNumber*メソッドのシーケンス番号と*CountOfSlots* v-table でスキップするスロットの数です。 場合*CountOfSlots*は省略すると、1 と見なされます。 これらのダミー メソッドはマネージまたはアンマネージ コードから呼び出すことであり、これらをマネージまたはアンマネージ コードから呼び出すしようとすると、例外が生成されます。 唯一の目的は、COM 統合サービスのランタイムを生成する v テーブルの領域を占有します。  
  
## <a name="duplicate-methods"></a>重複したメソッド  
 重複したメソッドを定義する必要があります。 つまり、呼び出す必要はありません`DefineMethod`重複する一連の値の`td`、 `wzName`、および`pvSig`パラメーター。 (これら 3 つのパラメーターを一意にメソッドを定義します。)。 設定されているのいずれかのメソッドの定義で、重複する 3 つの要素を使用するただし、`mdPrivateScope`ビット、`dwMethodFlags`パラメーター。 (、`mdPrivateScope`ビットは、コンパイラはこのメソッドの定義への参照を出力していないことを意味します)。  
  
## <a name="method-implementation-information"></a>メソッドの実装について  
 メソッドの実装に関する情報は、ほとんどの場合、メソッドの宣言時に呼ばれます。 そのため、必要はありませんで値を渡す、`ulCodeRVA`と`dwImplFlags`パラメーターを呼び出すときに`DefineMethod`です。 後でを通じて値を指定することができます[imetadataemit::setmethodimplflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)または[imetadataemit::setrva](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md) をクリックします。  
  
 プラットフォーム呼び出し (PInvoke) または COM 相互運用のシナリオなど、いくつかの状況で、メソッドの本体は指定しないで、および`ulCodeRVA`を 0 に設定する必要があります。 これらの状況でメソッドいないタグ付けするか抽象として、ランタイムは、実装を見つけるためです。  
  
## <a name="defining-a-method-for-pinvoke"></a>PInvoke のメソッドを定義します。  
 PInvoke によって呼び出される各アンマネージ関数の場合には、対象のアンマネージ関数を表すマネージ メソッドを定義する必要があります。 マネージ メソッドを定義するのには、使用`DefineMethod`PInvoke を使用する方法に応じて、特定の値に設定されたパラメーターの一部を。  
  
-   PInvoke の true - アンマネージ DLL 内にある外部のアンマネージ メソッドの呼び出しが含まれます。  
  
-   ローカル PInvoke - には、現在のマネージ モジュールに埋め込まれているネイティブのアンマネージ メソッドの呼び出しが含まれます。  
  
 パラメーターの設定は、次の表で表されます。  
  
|パラメーター|True の PInvoke の値|ローカルの PInvoke の値|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||設定`mdStatic`クリア;`mdSynchronized`と`mdAbstract`です。|  
|`pvSigBlob`|有効な共通言語ランタイム (CLR) メソッドのシグネチャに無効なパラメーターはマネージ型です。|有効なパラメーターを持つ有効な CLR メソッドのシグネチャはマネージ型です。|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|設定`miCil`と`miManaged`です。|設定`miNative`と`miUnmanaged`です。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
