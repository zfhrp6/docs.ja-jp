---
title: "方法: 埋め込みリソースにタイム ゾーンを保存"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 96dd3f0a3ed27a9e09c62f3ad4f450ced5a8e644
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>方法: 埋め込みリソースにタイム ゾーンを保存

多くの場合、タイム ゾーンに対応するアプリケーションでは、特定のタイム ゾーンが存在する必要があります。 ただし、ため個々 の可用性<xref:System.TimeZoneInfo>オブジェクトは、ローカル システムのレジストリに格納されている情報によって異なります、慣例的でも使用できるタイム ゾーンが存在しない可能性があります。 使用してさらに、カスタム タイム ゾーンに関する情報がインスタンス化、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドが他のタイム ゾーン情報がレジストリに保存されていません。 必要なときにこれらのタイム ゾーンが使用可能なであることを確認するをシリアル化するして保存し、それらを逆シリアル化して後で復元することができます。

通常、シリアル化する、<xref:System.TimeZoneInfo>オブジェクトが、タイム ゾーンに対応するアプリケーションとは別に発生します。 シリアル化された保持するために使用されるデータ ストアによって<xref:System.TimeZoneInfo>オブジェクト、(たとえば、レジストリのアプリケーション キーでデータが格納されている場合)、セットアップまたはインストール ルーチンの一部として、またはを実行するユーティリティ ルーチンの一部としては、タイム ゾーンのデータをシリアル化される可能性があります前に、(たとえば、シリアル化されたデータは .NET の XML リソース (.resx) ファイルに格納されている) 場合、最終的なアプリケーションがコンパイルされます。

ファイルに加え、リソース、アプリケーションでコンパイルされる、タイム ゾーン情報に関するその他のいくつかのデータ ストアを使用できます。 次に例を示します。

* レジストリです。 Hkey_local_machine NT\CurrentVersion\Time ゾーンのサブキーを使用するのではなく、カスタム タイム ゾーン データを格納するアプリケーションが独自のアプリケーション キーのサブキーを使用する必要があることに注意してください。

* 構成ファイル。

* その他のシステム ファイルです。

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>.Resx ファイルにシリアル化することによって、タイム ゾーンを保存するには

1. 既存のタイム ゾーンを取得するか、新しいタイム ゾーンを作成します。

   既存のタイム ゾーンを取得するには、次を参照してください。[する方法: 定義済みの UTC とローカル タイム ゾーン オブジェクトをアクセス](../../../docs/standard/datetime/access-utc-and-local.md)と[する方法: TimeZoneInfo オブジェクトをインスタンス化](../../../docs/standard/datetime/instantiate-time-zone-info.md)です。

   新しいタイム ゾーンを作成するには、オーバー ロードのいずれかを呼び出して、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドです。 詳細については、次を参照してください。[する方法: 調整規則のないタイム ゾーンを作成](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)と[する方法: 調整規則のあるタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)です。

2. 呼び出す、<xref:System.TimeZoneInfo.ToSerializedString%2A>タイム ゾーンのデータを含む文字列を作成するメソッド。

3. インスタンスを作成、<xref:System.IO.StreamWriter>オブジェクトの名前と必要に応じて、.resx ファイルへのパスを提供することによって、<xref:System.IO.StreamWriter>クラスのコンス トラクターです。

4. インスタンスを作成、<xref:System.Resources.ResXResourceWriter>オブジェクトを渡すことによって、<xref:System.IO.StreamWriter>オブジェクトを<xref:System.Resources.ResXResourceWriter>クラスのコンス トラクターです。

5. タイム ゾーンをパスする文字列をシリアル化、<xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType>メソッドです。

6. <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> メソッドを呼び出します。

7. <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> メソッドを呼び出します。

8. 閉じる、<xref:System.IO.StreamWriter>オブジェクトを呼び出してその<xref:System.IO.StreamWriter.Close%2A>メソッドです。

9. 生成された .resx ファイルをアプリケーションの Visual Studio プロジェクトに追加します。

10. 使用して、**プロパティ**Visual Studio で、ウィンドウことを確認して、.resx ファイルの**ビルド アクション**プロパティに設定されている**埋め込まれたリソース**です。

## <a name="example"></a>例

次の例のシリアル化、<xref:System.TimeZoneInfo>中部標準時を表すオブジェクト、および<xref:System.TimeZoneInfo>SerializedTimeZones.resx という名前の .NET XML リソース ファイルに Palmer ステーション、南極時間を表すオブジェクト。 中部標準時は通常、レジストリで定義されています。Palmer ステーション南極は、カスタム タイム ゾーンです。

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

この例のシリアル化<xref:System.TimeZoneInfo>オブジェクトを使用できるように、リソース ファイルにコンパイル時にします。

<xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType>メソッドは、.NET の XML リソース ファイルに完全なヘッダー情報を追加し、リソースを追加する既存のファイルを使用することはできません。 例では、これを処理 SerializedTimeZones.resx ファイルを確認して、存在する場合以外のすべてのリソースを格納する、2 つシリアル化されたジェネリック型にタイム ゾーン<xref:System.Collections.Generic.Dictionary%602>オブジェクト。 既存のファイルは削除し、され、既存のリソースが新しい SerializedTimeZones.resx ファイルに追加されます。 シリアル化されたタイム ゾーンのデータは、このファイルにも追加されます。

キー (または**名前**) リソースのフィールドは空白文字を含めることはできません。 <xref:System.String.Replace%28System.String%2CSystem.String%29>リソース ファイルに割り当てられている前に、タイム ゾーン識別子ですべての埋め込みスペースを削除するメソッドが呼び出されます。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

* System.Windows.Forms.dll および System.Core.dll への参照がプロジェクトに追加します。

* 次の名前空間は、インポートします。

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>関連項目

[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)
[する方法: 埋め込みリソースからタイム ゾーンを復元](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
