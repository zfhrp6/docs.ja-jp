---
title: IMetaDataDispenserEx::SetOption メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.SetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::SetOption
helpviewer_keywords:
- IMetaDataDispenserEx::SetOption method [.NET Framework metadata]
- SetOption method [.NET Framework metadata]
ms.assetid: 9f1c7ccd-7fb2-41d8-aa00-24b823376527
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cfe600b54eb03a07ea01375355c5ff94190e5d9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449469"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption メソッド
現在のメタデータ スコープに指定された値を指定されたオプションを設定します。 オプションは、現在のメタデータ スコープへの呼び出しの処理方法を制御します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetOption (  
    [in] REFGUID optionId,   
    [in] const VARIANT *pValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `optionId`  
 [in]設定するオプションを指定する GUID を指すポインター。  
  
 `pValue`  
 [in]オプションの設定に使用する値。 この値の型は、指定したオプションの種類のバリエーションである必要があります。  
  
## <a name="remarks"></a>コメント  
 次の表に、使用可能な Guid を`optionId`パラメーターが指すことができ、対応する有効な値の`pValue`パラメーター。  
  
|GUID|説明|`pValue` パラメーター|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|重複をチェックする項目を制御します。 呼び出すたびに、 [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)を新しい項目を作成するメソッドを現在のスコープ内の項目は既に存在するかどうかを確認するメソッドを依頼することができます。 存在を確認するなど、`mdMethodDef`項目です。 ここでは、呼び出す[imetadataemit::definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)、メソッドが、現在のスコープに存在ないことを確認します。 このチェックは、特定のメソッドを一意に識別するキーを使用して: 親の種類、名前、および署名されます。|UI4、型のバリアントをする必要があるありの値の組み合わせを含める必要があります、 [CorCheckDuplicatesFor](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md)列挙します。|  
|MetaDataRefToDefCheck|参照項目コントロールは、定義に変換されます。 既定では、メタデータ エンジンは、参照されているアイテムが実際には、現在のスコープで定義されている場合、その定義に参照されているアイテムを変換することで、コードが最適化されます。|UI4、型のバリアントをする必要があるありの値の組み合わせを含める必要があります、 [CorRefToDefCheck](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md)列挙します。|  
|MetaDataNotificationForTokenMovement|メタデータのマージ中に発生したトークンを再マップ コントロールは、コールバックを生成します。 使用して、 [imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)を構築する方法、 [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)インターフェイスです。|UI4、型のバリアントをする必要があるありの値の組み合わせを含める必要があります、 [CorNotificationForTokenMovement](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md)列挙します。|  
|MetaDataSetENC|エディット コンティニュ (ENC) の動作を制御します。 動作の 1 つのみのモードは、一度に設定できます。|UI4、型のバリアントをする必要があるありの値を含める必要があります、 [CorSetENC](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md)列挙します。 値はビットマスクではありません。|  
|MetaDataErrorIfEmitOutOfOrder|出力での順序不定エラー コールバックの生成を制御します。 誤順序のメタデータの生成致命的ではありません。ただし、メタデータ エンジンに適した順序でメタデータを出力する場合、メタデータがよりコンパクトなされためより効率的に検索できます。 使用して、`IMetaDataEmit::SetHandler`を構築する方法、 [IMetaDataError](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)インターフェイスです。|UI4、型のバリアントをする必要があるありの値の組み合わせを含める必要があります、 [CorErrorIfEmitOutOfOrder](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md)列挙します。|  
|MetaDataImportOption|列挙子によって取得 ENC 時に削除された項目の種類を制御します。|UI4、型のバリアントをする必要があるありの値の組み合わせを含める必要があります、 [CorImportOptions 列挙型](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md)列挙します。|  
|MetaDataThreadSafetyOptions|メタデータ エンジンが備わり、スレッド セーフ ロックについてリーダー/ライターを取得しているかどうかを制御します。 既定では、エンジンではアクセスが、呼び出し元がシングル スレッド ロックは取得されませんので前提としています。 クライアントは、メタデータ API を使用する場合は、適切なスレッドの同期を保守管理を担当します。|UI4、型のバリアントをする必要があるありの値を含める必要があります、 [CorThreadSafetyOptions](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md)列挙します。 値はビットマスクではありません。|  
|MetaDataGenerateTCEAdapters|タイプ ライブラリ インポーターで COM 接続ポイント コンテナーを密に結合されたイベント (TCE) アダプターを生成するかどうかを制御します。|BOOL 型のバリアントにする必要があります。 場合`pValue`に設定されている`true`、タイプ ライブラリ インポーターで TCE アダプターが生成されます。|  
|MetaDataTypeLibImportNamespace|インポートされるタイプ ライブラリの既定以外の名前空間を指定します。|Null 値または BSTR 型のバリアント型のいずれかにする必要があります。 場合`pValue`は、null 値に null。 それ以外の場合、現在の名前空間は設定されて、現在の名前空間は、バリアントの BSTR 型に保持されている文字列に設定されます。|  
|MetaDataLinkerOptions|リンカーが、アセンブリまたは .NET Framework モジュール ファイルを生成するかどうかを制御します。|UI4、型のバリアントをする必要があるありの値の組み合わせを含める必要があります、 [CorLinkerOptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md)列挙します。|  
|MetaDataRuntimeVersion|このイメージの作成対象となる共通言語ランタイムのバージョンを指定します。 バージョンは、"v1.0.3705"などの文字列として格納されます。|Null 値、VT_EMPTY 値、または BSTR 型のバリエーションがあります。 場合`pValue`が null の場合、ランタイムのバージョンが設定を null にします。 場合`pValue`VT_EMPTY には、バージョンが内部でメタデータのコードが実行されている Mscorwks.dll のバージョンから描画された既定値に設定します。 それ以外の場合、ランタイムのバージョンは、バリアントの BSTR 型に保持されている文字列に設定されます。|  
|MetaDataMergerOptions|メタデータのマージ オプションを指定します。|UI4、型のバリアントをする必要があるありの値の組み合わせを含める必要があります、`MergeFlags`列挙体は、CorHdr.h ファイルで説明します。|  
|MetaDataPreserveLocalRefs|定義にローカル参照の最適化を無効にします。|値の組み合わせを含める必要があります、 [CorLocalRefPreservation](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md)列挙します。|  
  
## <a name="requirements"></a>要件  
 **Platform:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataDispenserEx インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataDispenser インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
