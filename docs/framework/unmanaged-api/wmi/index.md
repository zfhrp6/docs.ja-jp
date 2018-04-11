---
title: WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)
description: .NET Framework の概要を示します WMI パフォーマンス カウンターに関する情報のアンマネージ API です。
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.date: 11/06/2017
ms.topic: reference
ms.prod: .net-framework
ms.devlang: cpp
ms.workload:
- dotnet
ms.openlocfilehash: c7959d6b6b7bafd728db5a579ff1376e686c5b74
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>Windows Management Instrumentation (WMI) およびパフォーマンス カウンター (アンマネージ API リファレンス)

.NET Framework WMI およびパフォーマンス カウンターのアンマネージ API の呼び出しをラップする関数のセットから構成、[ネイティブの Windows Management Instrumentation API](https://msdn.microsoft.com/library/aa389276(v=vs.85).aspx)です。 開発ツールとライブラリを管理したり、リモート コンピューターのシステムを監視することができます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
API には、次の関数が含まれています。

| 関数 | 説明 |
|---------|---------|
| [BeginEnumeration 関数](beginenumeration.md) | WMI オブジェクトのプロパティの列挙体の先頭に、列挙子をリセットします。 |
| [BeginMethodEnumeration 関数](beginmethodenumeration.md) |  オブジェクトの使用可能なメソッドの列挙を開始します。 |
| [BlessIWbemServices 関数](blessiwbemservices.md) | ユーザーの資格情報が指定した IWbemServices クラスへのアクセスを許可するかどうかを示します。 |
| [BlessIWbemServicesObject 関数](blessiwbemservicesobject.md) | ユーザーの資格情報が指定した IWbem サービス オブジェクトへのアクセスを許可するかどうかを示します。 |
| [Clone 関数](clone.md) | 現在のオブジェクトの完全な複製である新しいオブジェクトを返します。 |
| [CloneEnumWbemClassObject 関数](cloneenumwbemclassobject.md) | 列挙体の現在位置を保持、列挙子の論理コピーを作成します。 |
| [CompareTo 関数](compareto.md) | 別の Windows 管理オブジェクトにオブジェクトを比較します。 |
| [ConnectServerWmi 関数](connectserverwmi.md) | 指定したコンピューターで WMI 名前空間に使用する DCOM による接続を作成します。 |
| [CreateClassEnumWmi 関数](createclassenumwmi.md) | 指定した選択条件を満たすすべてのクラスの列挙子を返します。 |
| [CreateInstanceEnumWmi 関数](createinstanceenumwmi.md) | 指定したクラスの指定された選択条件を満たすためを返す列挙子を返します。 |
| [Delete 関数](delete.md) | クラスの定義とすべての修飾子から、指定したプロパティを削除します。 |
| [DeleteMethod 関数](deletemethod.md) | CIM クラス定義から、指定したメソッドを削除します。 |
| [EndEnumeration 関数](endenumeration.md) | 列挙のシーケンスを終了します。 | 
| [EndMethodEnumeration 関数](endmethodenumeration.md) | 呼び出しによって開始された列挙のシーケンスの終了、 [BeginMethodEnumeration 関数](beginmethodenumeration.md)です。 |
| [ExecNotificationQueryWmi 関数](execnotificationquerywmi.md) | イベントを受信するクエリを実行します。 |
| [ExecQueryWmi 関数](execquerywmi.md) | オブジェクトを取得するクエリを実行します。 |
| [FormatFromRawValue 関数](formatfromrawvalue.md) | 形式の変換が時間ベースの場合は、指定された形式に 1 つの生のパフォーマンス データの値または生のパフォーマンス データの 2 つの値に変換します。 | 
| [Get 関数](get.md) | 存在する場合は、指定したプロパティ値を取得します。 |
| [GetCurrentApartmentType 関数](getcurrentapartmenttype.md) | 呼び出し元を実行しているアパートメントの種類を取得します。 |
| [GetDemultiplexedStub 関数](getdemultiplexedstub.md) | Windows の管理から非同期呼び出しの受信をクライアントを支援するためには、オブジェクト転送シンクを作成します。 |
| [GetErrorInfo 関数](geterrorinfo.md) | 前の関数呼び出しからエラー情報を取得します。 | 
| [GetMethod 関数](getmethod.md) | 指定したメソッドに関する情報を取得します。 | 
| [GetMethodOrigin 関数](getmethodorigin.md) | メソッドが宣言されるクラスを決定します。 |
| [GetMethodQualifierSet 関数](getmethodqualifierset.md) | 特定のメソッドの設定、修飾子を取得します。 |
| [GetNames 関数](getnames.md) | 一部またはすべてのオブジェクトのプロパティの名前を取得します。 |
| [GetObjectText 関数](getobjecttext.md) | MOF 構文では、オブジェクトのテキストのレンダリングを返します。 | 
| [GetPropertyHandle 関数](getpropertyhandle.md) | プロパティを識別する一意のハンドルを返します。 |
| [GetPropertyOrigin 関数](getpropertyorigin.md) | プロパティが宣言されるクラスを決定します。 |
| [GetPropertyQualifierSet 関数](getpropertyqualifierset.md) | 特定のプロパティの設定、修飾子を取得します。  |
| [GetQualifierSet 関数](getqualifierset.md) | クラスのインスタンスまたはクラス定義の設定、修飾子を取得します。 |
| [InheritsFrom 関数](inheritsfrom.md) | 現在のクラスまたはインスタンスが指定された親クラスから派生するかどうかを判断します。 |
| [Initialize 関数](initialize.md) | WMI の初期化を実行します。 |
| [次の関数](next.md) | 列挙体では、次のプロパティを取得します。 | 
| [NextMethod 関数](nextmethod.md) | 列挙体の次のメソッドを取得します。 |
| [Put 関数](put.md) | 新しい値を名前付きプロパティを設定します。 |
| [PutClassWmi 関数](putclasswmi.md) | 新しいクラスを作成または既存のものを更新します。 |
| [PutInstanceWmi 関数](putinstancewmi.md) | 作成するか、既存のクラスのインスタンスを更新します。 インスタンスは、WMI リポジトリに書き込まれます。 |
| [PutMethod 関数](putmethod.md) | メソッドを作成します。 |
| [QualifierSet_BeginEnumeration 関数](qualifierset-beginenumeration.md) | 列挙体の先頭にオブジェクトの修飾子の列挙子をリセットします。 |
| [QualifierSet_Delete 関数](qualifierset-delete.md) | 名前で指定された修飾子を削除します。  |
| [QualifierSet_EndEnumeration 関数](qualifierset-endenumeration.md) | 呼び出しで開始された列挙の終了、`QualifierSet_BeginEnumeration`関数。 |
| [QualifierSet_Get 関数](qualifierset-get.md) | 指定した名前付き修飾子を取得します。  |
| [QualifierSet_GetNames 関数](qualifierset-getnames.md) | すべての修飾子のまたは現在のオブジェクトまたはプロパティから使用できる指定された修飾子の名前を取得します。 |
| [QualifierSet_Next 関数](qualifierset-next.md) | 呼び出しの使用を開始する列挙体の次の修飾子を取得、 [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)関数。 |
| [QualifierSet_Put 関数](qualifierset-put.md) | 名前付きの修飾子と値を書き込みます。 |
| [ResetSecurity 関数](resetsecurity.md) | 指定された権限借用トークンを現在のスレッドに割り当てます。 |
| [SetSecurity 関数](setsecurity.md) | 現在のスレッドに関連付けられている権限借用トークンを取得します。 |
| [SpawnDerivedClass 関数](spawnderivedclass.md) | 指定したオブジェクトから新しく派生クラス オブジェクトを作成します。 | 
| [SpawnInstance 関数](spawninstance.md) | クラスの新しいインスタンスを作成します。 |   
| [VerifyClient 関数](verifyclientkey.md) | により、クライアント キーは、適切なセキュリティ。 |
| [WritePropertyValue 関数](writepropertyvalue.md) | プロパティのハンドルによって識別されたプロパティに指定したバイト数を書き込みます。 |

 ## <a name="see-also"></a>関連項目
[アンマネージ API リファレンス](../index.md) 
