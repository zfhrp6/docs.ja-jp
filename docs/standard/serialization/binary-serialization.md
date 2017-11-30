---
title: "バイナリ シリアル化"
ms.date: 08/11/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
caps.latest.revision: "5"
author: ViktorHofer
ms.author: mairaw
ms.openlocfilehash: 74ee4e21934c1e4f3fd008664b1315429dc47b37
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="binary-serialization"></a>バイナリ シリアル化

シリアル化は、オブジェクトの状態をストレージ メディアに格納するプロセスとして定義することができます。 このプロセスの実行中に、オブジェクトのパブリックおよびプライベートなフィールドとクラス (クラスを格納しているアセンブリを含む) の名前がバイト ストリームに変換され、データ ストリームに書き込まれます。 続いてオブジェクトが逆シリアル化され、元のオブジェクトの完全な複製が作成されます。

オブジェクト指向環境でシリアル化機構を実装する場合は、使いやすさと柔軟性の間での数多くのトレードオフについて考慮する必要があります。 プロセスを十分に制御できる場合は、プロセスの大部分を自動化できます。 たとえば、単純なバイナリ シリアル化では不十分な状況が発生する場合や、シリアル化が必要なクラス内のフィールドを決定するだけの明確な理由がある場合があります。 以下のセクションでは、.NET に用意されている堅牢なシリアル化機構について検討し、必要に応じてプロセスをカスタマイズするためのいくつかの重要な機能について説明します。

> [!NOTE]
> オブジェクトのシリアル化と逆シリアル化を行う際に使用した .NET Framework のバージョンが異なる場合、UTF-8 または UTF-7 でエンコードされたオブジェクトの状態は保持されません。

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

バイナリ シリアル化の性質上、オブジェクト内でのプライベート メンバーの変更が可能であり、その状態が変化するため、パブリック API サーフェイスで動作する JSON.NET のような他のシリアル化フレームワークを使用することをお勧めします。

## <a name="binary-serialization-in-net-core"></a>.NET Core でのバイナリ シリアル化

.NET Core では、型のサブセットでのバイナリ シリアル化がサポートされます。 サポートされている型のリストは、「[シリアル化可能な型](#serializable-types)」で確認できます。 定義済みの一連の型は、.NET Framework 4.5.1 以降のバージョンと .NET Core 2.0 以降のバージョン間でシリアル化できることが保証されていいます。 Mono などの他の .NET 実装は公式にサポートされておらず、また機能もしません。

### <a name="serializable-types"></a>シリアル化可能な型

- <xref:System.AggregateException?displayProperty=nameWithType>   
- <xref:System.Array?displayProperty=nameWithType>   
- <xref:System.ArraySegment%601?displayProperty=nameWithType>   
- <xref:System.Attribute?displayProperty=nameWithType>   
- <xref:System.Boolean?displayProperty=nameWithType>   
- <xref:System.Byte?displayProperty=nameWithType>   
- <xref:System.Char?displayProperty=nameWithType>   
- <xref:System.Collections.ArrayList?displayProperty=nameWithType>   
- <xref:System.Collections.BitArray?displayProperty=nameWithType>   
- <xref:System.Collections.Comparer?displayProperty=nameWithType>   
- <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType>   
- <xref:System.Collections.Hashtable?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.Queue?displayProperty=nameWithType>   
- <xref:System.Collections.SortedList?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Stack?displayProperty=nameWithType>   
- <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType>   
- <xref:System.DBNull?displayProperty=nameWithType>(.NET Core 2.0.2 とそれ以降のバージョンで使用可能)   
- <xref:System.Data.DataSet?displayProperty=nameWithType>   
- <xref:System.Data.DataTable?displayProperty=nameWithType>   
- <xref:System.Data.PropertyCollection?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType>   
- <xref:System.DateTime?displayProperty=nameWithType>   
- <xref:System.DateTimeOffset?displayProperty=nameWithType>   
- <xref:System.Decimal?displayProperty=nameWithType>   
- <xref:System.Double?displayProperty=nameWithType>   
- <xref:System.Drawing.Color?displayProperty=nameWithType>   
- <xref:System.Drawing.Point?displayProperty=nameWithType>   
- <xref:System.Drawing.PointF?displayProperty=nameWithType>   
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>   
- <xref:System.Drawing.RectangleF?displayProperty=nameWithType>   
- <xref:System.Drawing.Size?displayProperty=nameWithType>   
- <xref:System.Drawing.SizeF?displayProperty=nameWithType>   
- <xref:System.Enum?displayProperty=nameWithType>   
- <xref:System.Exception?displayProperty=nameWithType>   
- <xref:System.Globalization.CompareInfo?displayProperty=nameWithType>   
- <xref:System.Globalization.SortVersion?displayProperty=nameWithType>   
- <xref:System.Guid?displayProperty=nameWithType>   
- <xref:System.Int16?displayProperty=nameWithType>   
- <xref:System.Int32?displayProperty=nameWithType>   
- <xref:System.Int64?displayProperty=nameWithType>   
- <xref:System.IntPtr?displayProperty=nameWithType>   
- <xref:System.Net.Cookie?displayProperty=nameWithType>   
- <xref:System.Net.CookieCollection?displayProperty=nameWithType>   
- <xref:System.Net.CookieContainer?displayProperty=nameWithType>   
- <xref:System.Nullable%601?displayProperty=nameWithType>   
- <xref:System.Numerics.BigInteger?displayProperty=nameWithType>   
- <xref:System.Numerics.Complex?displayProperty=nameWithType>   
- <xref:System.Object?displayProperty=nameWithType>   
- <xref:System.SByte?displayProperty=nameWithType>   
- <xref:System.Single?displayProperty=nameWithType>   
- <xref:System.String?displayProperty=nameWithType>   
- <xref:System.StringComparer?displayProperty=nameWithType>   
- <xref:System.Text.StringBuilder?displayProperty=nameWithType>   
- <xref:System.TimeSpan?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType>   
- <xref:System.Tuple?displayProperty=nameWithType>   
- <xref:System.UInt16?displayProperty=nameWithType>   
- <xref:System.UInt32?displayProperty=nameWithType>   
- <xref:System.UInt64?displayProperty=nameWithType>   
- <xref:System.UIntPtr?displayProperty=nameWithType>   
- <xref:System.Uri?displayProperty=nameWithType>   
- <xref:System.ValueTuple?displayProperty=nameWithType>(いない .NET Framework 4.7 と以前のバージョンでシリアル化可能)  
- <xref:System.ValueType?displayProperty=nameWithType>   
- <xref:System.Version?displayProperty=nameWithType>   
- <xref:System.WeakReference?displayProperty=nameWithType>   
- <xref:System.WeakReference%601?displayProperty=nameWithType>   

## <a name="in-this-section"></a>このセクションの内容

 [シリアル化の概念](../../../docs/standard/serialization/serialization-concepts.md)  
 データをストレージに永続化するシナリオと、アプリケーション ドメインを越えてオブジェクトを受け渡しするシナリオの 2 つを例として、シリアル化の有効な利用方法について説明します。  
  
 [基本的なシリアル化](../../../docs/standard/serialization/basic-serialization.md)  
 バイナリ フォーマッタと SOAP フォーマッタを使用してオブジェクトをシリアル化する方法について説明します。  
  
 [選択的シリアル化](../../../docs/standard/serialization/selective-serialization.md)  
 クラスの一部のメンバーがシリアル化されないようにする方法について説明します。  
  
 [カスタムのシリアル化](../../../docs/standard/serialization/custom-serialization.md)  
 <xref:System.Runtime.Serialization.ISerializable> インターフェイスを使用してクラスのシリアル化をカスタマイズする方法について説明します。  
  
 [シリアル化プロセスの手順](../../../docs/standard/serialization/steps-in-the-serialization-process.md)  
 フォーマッタで <xref:System.Runtime.Serialization.Formatter.Serialize%2A> メソッドを呼び出した場合のシリアル化方法について説明します。  
  
 [バージョン トレラントなシリアル化](../../../docs/standard/serialization/version-tolerant-serialization.md)  
 アプリケーションに例外をスローさせることなく後から変更できる、シリアル化可能な型の作成方法について説明します。  
  
 [シリアル化のガイドライン](../../../docs/standard/serialization/serialization-guidelines.md)  
 オブジェクトをシリアル化するタイミングを決定するのに役立つ、いくつかの一般的なガイドラインを示します。  
  
## <a name="reference"></a>参照  
 <xref:System.Runtime.Serialization>  
 オブジェクトのシリアル化と逆シリアル化に使用できるクラスが含まれています。  
  
## <a name="related-sections"></a>関連項目  
 [XML シリアル化および SOAP シリアル化](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 共通言語ランタイムに付属している XML シリアル化機構について説明します。  
  
 [セキュリティとシリアル化](../../../docs/framework/misc/security-and-serialization.md)  
 シリアル化を実行するコードを記述する際に従う必要がある、安全なコーディングのガイドラインについて説明します。  
  
 [リモート オブジェクト](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58)  
 .NET Framework でリモート通信に利用できるさまざまな通信方法について説明します。  
  
 [ASP.NET と XML Web サービス クライアントを使用して作成した XML Web サービス](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 ASP.NET を使用して作成した XML Web サービスのプログラミング方法について説明するトピックを示します。
