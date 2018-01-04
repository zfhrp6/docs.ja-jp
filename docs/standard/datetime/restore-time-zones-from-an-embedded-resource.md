---
title: "方法: 埋め込みリソースからタイム ゾーンを復元"
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
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: efb133d972427a9619581d0670268cba9fbd3ee6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>方法: 埋め込みリソースからタイム ゾーンを復元

このトピックでは、リソース ファイルに保存されているタイム ゾーンを復元する方法について説明します。 タイム ゾーンを保存する方法についてを参照してください[する方法: 埋め込みリソースにタイム ゾーンを保存](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)です。

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>埋め込みリソースから TimeZoneInfo オブジェクトを逆シリアル化するには

1. 取得するタイム ゾーンが、カスタム タイム ゾーンでない場合は、インスタンス化しようとそれを使用して、<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>メソッドです。

2. インスタンスを作成、<xref:System.Resources.ResourceManager>埋め込みリソース ファイルとリソース ファイルを格納するアセンブリへの参照の完全修飾名を渡すことによってオブジェクト。

   使用して、埋め込みリソース ファイルの完全修飾名を特定できない場合、 [Ildasm.exe (IL 逆アセンブラー)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)アセンブリのマニフェストを検査します。 `.mresource`エントリは、リソースを識別します。 リソースの完全修飾名は、例では、`SerializeTimeZoneData.SerializedTimeZones`です。

   呼び出してへの参照を取得するには、リソース ファイルがタイム ゾーンのインスタンス化コードを含む同じアセンブリに埋め込まれている場合、 `static` (`Shared` Visual Basic で)<xref:System.Reflection.Assembly.GetExecutingAssembly%2A>メソッドです。

3. 場合への呼び出し、<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>メソッドが失敗する、または、カスタム タイム ゾーンをインスタンス化する場合は、呼び出すことによって、シリアル化されたタイム ゾーンを表す文字列を取得、<xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>メソッドです。

4. 呼び出して、タイム ゾーン データを逆シリアル化、<xref:System.TimeZoneInfo.FromSerializedString%2A>メソッドです。

## <a name="example"></a>例

次の例を逆シリアル化、<xref:System.TimeZoneInfo>埋め込み .NET XML リソース ファイルに格納されているオブジェクト。

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

このコードは、ことを確認する例外処理を示しています、<xref:System.TimeZoneInfo>アプリケーションで必要なオブジェクトが存在します。 最初のインスタンスを作成しよう、<xref:System.TimeZoneInfo>オブジェクトを使用して、レジストリから取得して、<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>メソッドです。 タイム ゾーンをインスタンス化できない場合は、埋め込みリソース ファイルから取得します。

カスタム タイム ゾーンのデータ (タイム ゾーンを使用してインスタンス化、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッド) が保存されていないレジストリで、コードを呼び出すことはできません、 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> Palmer、南極のタイム ゾーンをインスタンス化します。 代わりに、すぐに見た目を呼び出す前に、タイム ゾーンのデータを含む文字列を取得する埋め込みリソース ファイルを<xref:System.TimeZoneInfo.FromSerializedString%2A>メソッドです。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

* System.Windows.Forms.dll および System.Core.dll への参照がプロジェクトに追加します。

* 次の名前空間は、インポートします。

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>関連項目

[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)
[する方法: 埋め込みリソースにタイム ゾーンを保存](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
