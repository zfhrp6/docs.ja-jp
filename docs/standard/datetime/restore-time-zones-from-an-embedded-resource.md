---
title: "方法 : 埋め込みリソースからタイム ゾーンを復元する | Microsoft Docs"
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
  - "タイム ゾーン [.NET Framework], 逆シリアル化"
  - "タイム ゾーン [.NET Framework], 復元"
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : 埋め込みリソースからタイム ゾーンを復元する
このトピックでは、リソース ファイルに保存されているタイム ゾーンを復元する方法について説明します。  タイム ゾーンの保存に関する詳細と方法については、「[方法 : 埋め込みリソースにタイム ゾーンを保存する](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)」を参照してください。  
  
### 埋め込みリソースから TimeZoneInfo オブジェクトを逆シリアル化するには  
  
1.  取得するタイム ゾーンがカスタム タイム ゾーンではない場合は、<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> メソッドを使用してインスタンス化を試みます。  
  
2.  埋め込みリソース ファイルの完全修飾名およびリソース ファイルを含むアセンブリへの参照を渡して、<xref:System.Resources.ResourceManager> オブジェクトをインスタンス化します。  
  
     埋め込みリソース ファイルの完全修飾名がわからない場合は、[Ildasm.exe \(IL 逆アセンブラー\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) を使用してアセンブリのマニフェストを調べます。  `.mresource` エントリがリソースを示しています。  この例では、リソースの完全修飾名は `SerializeTimeZoneData.SerializedTimeZones` です。  
  
     リソース ファイルが、タイム ゾーンのインスタンス化コードと同じアセンブリに埋め込まれている場合は、`static` \(Visual Basic では `Shared`\) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> メソッドを呼び出すことで、リソース ファイルへの参照を取得できます。  
  
3.  <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> メソッドの呼び出しが失敗する場合、またはカスタム タイム ゾーンをインスタンス化する場合は、<xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName> メソッドを呼び出して、シリアル化されたタイム ゾーンを含む文字列を取得します。  
  
4.  <xref:System.TimeZoneInfo.FromSerializedString%2A> メソッドを呼び出して、タイム ゾーン データを逆シリアル化します。  
  
## 使用例  
 次の例では、埋め込み .NET XML リソース ファイルに格納されている <xref:System.TimeZoneInfo> オブジェクトを逆シリアル化します。  
  
 [!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
 [!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]  
  
 このコードは、アプリケーションで必要な <xref:System.TimeZoneInfo> オブジェクトが存在することを確認するための例外処理を示しています。  最初に、<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> メソッドを使用してレジストリから取得する方法で、<xref:System.TimeZoneInfo> オブジェクトのインスタンス化を試みます。  タイム ゾーンをインスタンス化できない場合は、埋め込みリソース ファイルから取得します。  
  
 カスタム タイム ゾーン \(<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを使用してインスタンス化されるタイム ゾーン\) のデータはレジストリに格納されていないので、Palmer, Antarctica のタイム ゾーンをインスタンス化するときは <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> を呼び出しません。  代わりに、<xref:System.TimeZoneInfo.FromSerializedString%2A> メソッドを呼び出す前に、埋め込みリソース ファイルを直接調べてタイム ゾーンのデータを含む文字列を取得します。  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System.Windows.Forms.dll および System.Core.dll への参照をプロジェクトに追加する。  
  
-   次の名前空間をインポートする。  
  
     [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
     [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]  
  
## 参照  
 [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)   
 [タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)   
 [方法 : 埋め込みリソースにタイム ゾーンを保存する](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)