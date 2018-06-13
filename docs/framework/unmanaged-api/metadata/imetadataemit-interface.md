---
title: IMetaDataEmit インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit
helpviewer_keywords:
- IMetaDataEmit interface [.NET Framework metadata]
ms.assetid: 3b48fd47-7397-4e2c-8bec-8157aa08978c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4c77edfff640f796dd3f345eaeb4728830c5f4c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449145"
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit インターフェイス
作成、変更、および現在定義されているスコープ内でアセンブリに関するメタデータを保存する方法を提供します。 メタデータをメモリに格納されているまたはディスクに保存できます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ApplyEditAndContinue メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)|指定したで行われた変更を現在のアセンブリのスコープを更新`pImport`です。|  
|[DefineCustomAttribute メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)|指定したオブジェクトにアタッチされている、指定したメタデータ シグネチャを持つカスタム属性の定義を作成し、そのカスタム属性定義トークンを取得します。|  
|[DefineEvent メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)|指定したメタデータ シグネチャを持つイベントの定義を作成し、そのイベント定義トークンを取得します。|  
|[DefineField メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definefield-method.md)|指定したメタデータ シグネチャを持つフィールドの定義を作成し、そのフィールド定義トークンを取得します。|  
|[DefineImportMember メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)|現在のスコープ外にあるモジュールで定義され、その参照の定義のトークンを取得する型のメンバーの定義を作成します。|  
|[DefineImportType メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)|現在のスコープ外にあるモジュールで定義され、その参照定義トークンを取得する型への参照の定義を作成します。|  
|[DefineMemberRef メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)|現在のスコープ外にあるモジュールのメンバーへの参照の定義を作成し、その参照定義トークンを取得します。|  
|[DefineMethod メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)|指定したシグネチャを持つメソッドの定義を作成し、そのメソッドの定義にトークンを返します。|  
|[DefineMethodImpl メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethodimpl-method.md)|インターフェイスから継承されたメソッドの実装の定義を作成し、そのメソッドの実装定義にトークンを返します。|  
|[DefineModuleRef メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)|指定した名前のモジュールのメタデータ署名を作成します。|  
|[DefineNestedType メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definenestedtype-method.md)|型定義のメタデータ署名を作成し、返します、`mdTypeDef`さらに、定義済みの型によって参照される型のメンバーであることを指定する、その型のトークン`tdEncloser`です。|  
|[DefineParam メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)|指定したトークンによって参照されるメソッドの指定したシグネチャを持つパラメーターの定義を作成し、そのパラメーターの定義のトークンを取得します。|  
|[DefinePermissionSet メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)|アクセス許可が、指定したメタデータ シグネチャを持つ、設定の定義を作成し、そのアクセス許可セットの定義にトークンを取得します。|  
|[DefinePinvokeMap メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)|指定したトークンによって参照されるメソッドの PInvoke シグネチャの機能を設定します。|  
|[DefineProperty メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)|指定した、指定した型のプロパティ定義を作成`get`と`set`メソッド アクセサーし、そのプロパティ定義トークンを取得します。|  
|[DefineSecurityAttributeSet メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definesecurityattributeset-method.md)|指定したトークンによって参照されるオブジェクトにアタッチするセキュリティ権限のセットを作成します。|  
|[DefineTypeDef メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)|共通言語ランタイムの型の型定義を作成し、その種類の定義のメタデータ トークンを取得します。|  
|[DefineTypeRefByName メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)|現在のスコープ外の別のモジュールで定義されている型のメタデータ トークンを取得します。|  
|[DefineUserString メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)|指定されたリテラル文字列のメタデータ トークンを取得します。|  
|[DeleteClassLayout メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deleteclasslayout-method.md)|指定したトークンによって参照される型のクラス レイアウト メタデータ シグネチャを破棄します。|  
|[DeleteFieldMarshal メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletefieldmarshal-method.md)|指定したトークンによって参照されるオブジェクトのメタデータ シグネチャのマーシャ リング PInvoke を破棄します。|  
|[DeletePinvokeMap メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletepinvokemap-method.md)|指定したトークンによって参照されるオブジェクトの PInvoke マッピング メタデータを破棄します。|  
|[DeleteToken メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletetoken-method.md)|現在のメタデータ スコープから、指定されたトークンを削除します。|  
|[GetSaveSize メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-getsavesize-method.md)|現在のスコープ内には、バイナリ サイズの見積もり、アセンブリを取得します。|  
|[GetTokenFromSig メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)|指定されたメタデータ署名のトークンを取得します。|  
|[GetTokenFromTypeSpec メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)|指定したメタデータ シグネチャを持つ型のメタデータ トークンを取得します。|  
|[Merge メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)|指定されたインポートされたスコープをマージするスコープの一覧に追加します。|  
|[MergeEnd メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)|現在のマージのスコープを 1 つまたは複数の以前の呼び出しで指定されたすべてのメタデータ スコープ`IMetaDataEmit::Merge`です。|  
|[Save メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-save-method.md)|指定したアドレスにファイルを現在のスコープ内のすべてのメタデータを保存します。|  
|[SaveToMemory メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)|指定したメモリ領域を現在のスコープ内のすべてのメタデータを保存します。|  
|[SaveToStream メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)|現在のスコープを指定したすべてのメタデータを保存`IStream`です。|  
|[SetClassLayout メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)|設定または前回の呼び出しによって定義された型のクラス レイアウト シグネチャを更新`IMetaDataEmit::DefineTypeDef`です。|  
|[SetCustomAttributeValue メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setcustomattributevalue-method.md)|設定または前回の呼び出しによって定義されたカスタム属性の値を更新`IMetaDataEmit::DefineCustomAttribute`です。|  
|[SetEventProps メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-seteventprops-method.md)|前回の呼び出しによって定義されたイベントの指定した機能の更新を設定または`IMetaDataEmit::DefineEvent`です。|  
|[SetFieldMarshal メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldmarshal-method.md)|指定したトークンによって参照されるフィールド、メソッドの戻り値、またはメソッドのパラメーターのマーシャ リング情報 PInvoke に設定します。|  
|[SetFieldProps メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldprops-method.md)|設定または指定したフィールドのトークンによって参照されるフィールドの既定値を更新します。|  
|[SetFieldRVA メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldrva-method.md)|指定したトークンによって参照されるフィールドの相対仮想アドレスのグローバル変数の値を設定します。|  
|[SetHandler メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)|指定したによって参照されるメソッドを設定`IUnknown`トークンを再マップの通知のコールバックとしてのポインター。|  
|[SetMethodImplFlags メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)|設定または指定したトークンによって参照されている継承されたメソッドの実装のメタデータ シグネチャを更新します。|  
|[SetMethodProps メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodprops-method.md)|設定または、指定の相対仮想アドレス、前回の呼び出しによって定義されたメソッドに格納されている、この機能を更新`IMetaDataEmit::DefineMethod`です。|  
|[SetModuleProps メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)|前回の呼び出しで定義されているモジュールへの参照を更新`IMetaDataEmit::DefineModuleRef`です。|  
|[SetParamProps メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)|前回の呼び出しで定義されているメソッドのパラメーターの機能の変更を設定または`IMetaDataEmit::DefineParam`です。|  
|[SetParent メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparent-method.md)|確立する前回の呼び出しで定義されている、指定されたメンバー `IMetaDataEmit::DefineMemberRef`、前回の呼び出しで定義されている、指定した型のメンバーである`IMetaDataEmit::DefineTypeDef`です。|  
|[SetPermissionSetProps メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpermissionsetprops-method.md)|設定または前回の呼び出しによって定義されたアクセス許可セットのメタデータ署名の機能を更新`IMetaDataEmit::DefinePermissionSet`です。|  
|[SetPinvokeMap メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpinvokemap-method.md)|前回の呼び出しで定義されているメソッドの PInvoke シグネチャの機能の変更を設定または`IMetaDataEmit::DefinePinvokeMap`です。|  
|[SetPropertyProps メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpropertyprops-method.md)|前回の呼び出しによって定義されたプロパティのメタデータに格納されている機能の設定`IMetaDataEmit::DefineProperty`です。|  
|[SetRVA メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)|指定したメソッドの相対仮想アドレスを設定します。|  
|[SetTypeDefProps メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-settypedefprops-method.md)|前回の呼び出しによって定義された型の機能を設定`IMetaDataEmit::DefineTypeDef`です。|  
|[TranslateSigWithScope メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-translatesigwithscope-method.md)|現在のスコープにアセンブリをインポートし、マージされたスコープの新しいメタデータ シグネチャを取得します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
