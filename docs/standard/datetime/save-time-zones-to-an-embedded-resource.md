---
title: "方法 : 埋め込みリソースにタイム ゾーンを保存する | Microsoft Docs"
ms.custom: ""
ms.date: "04/10/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "タイム ゾーン オブジェクト [.NET Framework], 保存"
  - "タイム ゾーン オブジェクト [.NET Framework], シリアル化"
  - "タイム ゾーン [.NET Framework], 保存"
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : 埋め込みリソースにタイム ゾーンを保存する
タイム ゾーンに対応したアプリケーションでは、多くの場合、特定のタイム ゾーンが存在する必要があります。  しかし、個別の <xref:System.TimeZoneInfo> オブジェクトを使用できるかどうかはローカル システムのレジストリに格納されている情報に依存するので、通常は使用できるタイム ゾーンであっても存在しない場合があります。  さらに、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを使用することでインスタンス化されるカスタム タイム ゾーンについての情報は、他のタイム ゾーン情報とは異なりレジストリに格納されません。  このようなタイム ゾーンを必要なときに確実に使用できるようにするには、タイム ゾーンをシリアル化して保存し、必要になったら逆シリアル化して復元します。  
  
 通常、<xref:System.TimeZoneInfo> オブジェクトのシリアル化は、タイム ゾーンに対応するアプリケーションとは関係なく行われます。  シリアル化された <xref:System.TimeZoneInfo> オブジェクトの保持に使用するデータ ストアによっては、セットアップ ルーチンまたはインストール ルーチンの一部として \(たとえば、データがレジストリのアプリケーション キーに格納されるとき\)、または最終的なアプリケーションがコンパイルされる前に実行するユーティリティ ルーチンの一部として \(たとえば、シリアル化されたデータが .NET XML リソース \(.resx\) ファイルに格納されるとき\)、タイム ゾーンのデータをシリアル化できます。  
  
 アプリケーションと共にコンパイルされるリソース ファイル以外に、複数のデータ ストアをタイム ゾーン情報に使用できます。  次に例を示します。  
  
-   レジストリ。  アプリケーションでは、HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\Time Zones というサブキーを使用するのではなく、アプリケーション自体のキーのサブキーを使用してカスタム タイム ゾーン データを格納する必要があります。  
  
-   構成ファイル。  
  
-   その他のシステム ファイル。  
  
### .resx ファイルにシリアル化してタイム ゾーンを保存するには  
  
1.  既存のタイム ゾーンを取得するか、新しいタイム ゾーンを作成します。  
  
     既存のタイム ゾーンを取得する方法については、「[方法 : 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする](../../../docs/standard/datetime/access-utc-and-local.md)」および「[方法 : TimeZoneInfo オブジェクトをインスタンス化する](../../../docs/standard/datetime/instantiate-time-zone-info.md)」を参照してください。  
  
     新しいタイム ゾーンを作成するには、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドのオーバーロードの 1 つを呼び出します。  詳細については、「[方法 : 調整規則のないタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)」および「[方法 : 調整規則のあるタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)」を参照してください。  
  
2.  <xref:System.TimeZoneInfo.ToSerializedString%2A> メソッドを呼び出して、タイム ゾーンのデータを含む文字列を作成します。  
  
3.  .resx ファイルの名前、および必要に応じてファイルへのパスを <xref:System.IO.StreamWriter> クラスのコンストラクターに渡して、<xref:System.IO.StreamWriter> オブジェクトをインスタンス化します。  
  
4.  <xref:System.IO.StreamWriter> オブジェクトを <xref:System.Resources.ResXResourceWriter> クラスのコンストラクターに渡して、<xref:System.Resources.ResXResourceWriter> オブジェクトをインスタンス化します。  
  
5.  タイム ゾーンのシリアル化された文字列を、<xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=fullName> メソッドに渡します。  
  
6.  <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=fullName> メソッドを呼び出します。  
  
7.  <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=fullName> メソッドを呼び出します。  
  
8.  <xref:System.IO.StreamWriter.Close%2A> メソッドを呼び出して、<xref:System.IO.StreamWriter> オブジェクトを閉じます。  
  
9. 生成された .resx ファイルを、アプリケーションの Visual Studio プロジェクトに追加します。  
  
10. Visual Studio の **\[プロパティ\]** ウィンドウを使用して、.resx ファイルの **\[ビルド アクション\]** プロパティが **\[埋め込まれたリソース\]** に設定されていることを確認します。  
  
## 使用例  
 次の例では、中部標準時を表す <xref:System.TimeZoneInfo> オブジェクトと、Palmer Station, Antarctica 時刻を表す <xref:System.TimeZoneInfo> オブジェクトを、SerializedTimeZones.resx という名前の .NET XML リソース ファイルにシリアル化します。  普通、中部標準時はレジストリで定義されています。Palmer Station, Antarctica はカスタム タイム ゾーンです。  
  
 [!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
 [!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]  
  
 この例では、コンパイル時にリソース ファイルで使用できるように <xref:System.TimeZoneInfo> オブジェクトをシリアル化します。  
  
 <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=fullName> メソッドは完全なヘッダー情報を .NET XML リソース ファイルに追加するので、既存のファイルにリソースを追加するためには使用できません。  この例では、SerializedTimeZones.resx ファイルを検査することでこのことに対処しています。ファイルが存在する場合は、シリアル化した 2 つのタイム ゾーン以外のすべてのリソースを、汎用の <xref:System.Collections.Generic.Dictionary%602> オブジェクトに格納します。  その後、既存のファイルを削除し、既存のリソースを新しい SerializedTimeZones.resx ファイルに追加します。  シリアル化したタイム ゾーンのデータも、このファイルに追加します。  
  
 リソースのキー \(つまり **\[名前\]**\) フィールドでは、空白を含む文字列は指定できません。  タイム ゾーン識別子をリソース ファイルに割り当てる前に、<xref:System.String.Replace%28System.String%2CSystem.String%29> メソッドを呼び出して識別子に含まれるすべての空白を除去します。  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System.Windows.Forms.dll および System.Core.dll への参照をプロジェクトに追加する。  
  
-   次の名前空間をインポートする。  
  
     [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
     [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]  
  
## 参照  
 [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)   
 [タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)   
 [方法 : 埋め込みリソースからタイム ゾーンを復元する](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)