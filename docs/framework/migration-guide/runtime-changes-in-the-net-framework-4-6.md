---
title: ".NET Framework 4.6 におけるランタイムの変更点 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5262bcfa-6e48-416b-8972-69cb4002d386
caps.latest.revision: 34
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# .NET Framework 4.6 におけるランタイムの変更点
まれに、ランタイムの変更が、.NET Framework の以前のバージョンをターゲットとするものの、それ以降のバージョンの .NET Framework ランタイムで実行される既存のアプリに影響を与える可能性があります。 また、異なる .NET Framework ランタイム環境で実行されるアプリケーション間での動作に違いが生じます。 次の領域の変更が含まれています。  
  
-   [コア](#Core)  
  
-   [ネットワーク](#Networking)  
  
-   [Windows Presentation Foundation \(WPF\)](#WPF)  
  
-   [セットアップと配置](#Setup)  
  
-   [ClickOnce](#ClickOnce)  
  
-   [新しい 64 ビット JIT コンパイラ](#RyuJIT)  
  
<a name="Core"></a>   
## コア  
  
|機能|変更|影響|スコープ|  
|--------|--------|--------|----------|  
|<xref:System.Globalization.PersianCalendar?displayProperty=fullName>|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 以降では、<xref:System.Globalization.PersianCalendar> クラスはイスラム暦の太陽アルゴリズムを使用します。|イスラム暦の太陽アルゴリズムでは、イランとアフガニスタンで現在使用されているペルシャ暦と同じ結果が生成されます。 また、グレゴリオ暦の 1800 年からグレゴリオ暦の 2023 年の日付について、以前のアルゴリズムと同じ日付が生成されます。 この範囲外の日付については、<xref:System.Globalization.PersianCalendar> クラスを使用して日付を変換する \(たとえば、グレゴリオ暦の日付とペルシャ暦の日付の間で\) 場合や、特定の年がうるう年かどうかを決定する場合に影響を受けることがあります。<br /><br /> この変更を理由として、[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] がインストールされているシステムで <xref:System.Globalization.PersianCalendar.MinSupportedDateTime%2A?displayProperty=fullName> プロパティの値が 0622 年 3 月 21 日から 0622 年 3 月 22 日に変更されました。<br /><br /> 詳細については、「<xref:System.Globalization.PersianCalendar>」を参照してください。|マイナー|  
|<xref:System.Runtime.Versioning.TargetFrameworkAttribute>|既定のアプリケーション ドメインに関しては、<xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> プロパティの値は <xref:System.Runtime.Versioning.TargetFrameworkAttribute> が存在する場合にはこの属性から派生します。ただし、<xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> プロパティに対して名前が割り当てられて明示的に定義されている場合は除きます。  .NET Framework の以前のバージョンでは、<xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> 属性の値は `null` でした。ただし、<xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> プロパティでターゲット フレームワークを明示的に指定しないで、さまざまな特別なコード パスを実行したり、既定以外のアプリ ドメインを作成したりする場合は除きます。<br /><br /> 既定以外のアプリケーション ドメインの場合、<xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> プロパティの値の決定方法に変更はありません。<xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> プロパティに明示的に値が割り当てられていない場合、既定以外のアプリ ドメインは既定のアプリケーション ドメインからターゲット フレームワークの名前を継承します。|既定のアプリケーション ドメインの場合、<xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> はこれまでは `null` を返していましたが、null 以外の値を返すことあります。 これは、適切な動作です。|エッジ|  
|<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString%28System.Boolean%29?displayProperty=fullName>|システムにインストールされている証明書が .NET Framework でサポートされていない場合、`verbose` 引数で `True` 値を渡すと有効な文字列が返されます。 .NET Framework の以前のバージョンでは、サポートされていない証明書の公開キーの情報にアクセスしようとすると、例外がスローされることがあります。|このメソッドは情報提供のみが目的で、ドキュメントは .NET Framework のバージョン間で出力に一貫性がない場合があることを示しています。 この変更が影響を及ぼすのは、`ToString(True)` メソッドを呼び出し、.NET Framework によってサポートされていない証明書がインストールされているアプリに対してのみです。 この変更で例外をスローするのではなく文字列を返すことにより、メソッドがより堅牢になっています。|エッジ|  
|リフレクションと分散 COM \(DCOM\)|リフレクション オブジェクトはマネージ コードからアウト プロセス DCOM クライアントに渡されなくなりました。 以下の型が影響を受けます。<xref:System.Reflection.Assembly>; <xref:System.Reflection.MemberInfo> およびその派生型 \(<xref:System.Reflection.FieldInfo>、<xref:System.Reflection.MethodInfo><xref:System.Type>、<xref:System.Reflection.TypeInfo> を含む\); <xref:System.Reflection.MethodBody>; <xref:System.Reflection.Module>; <xref:System.Reflection.ParameterInfo>。|このオブジェクトの [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707.aspx) を呼び出すと `E_NOINTERFACE` が返されます。|マイナー|  
  
<a name="Networking"></a>   
## ネットワーク  
  
|機能|変更|影響|スコープ|  
|--------|--------|--------|----------|  
|<xref:System.Net.Mime.ContentDisposition?displayProperty=fullName> クラスの日付と時刻の値。|[RFC822](http://www.ietf.org/rfc/rfc0822.txt) と [RFC2822](http://www.ietf.org/rfc/rfc2822.txt) に準拠するため、書式設定された日付と時刻の値には 2 桁の時刻が含まれるようになりました。 以前は、午前 10時 00分より前の時間は 1 桁で表されていました。|この変更は、次のような使用シナリオに影響します。<br /><br /> -   .NET Framework の異なるバージョン間でシリアル化された <xref:System.Net.Mime.ContentDisposition> オブジェクトの長さやハッシュ コードを比較する場合。<br />-   .NET Framework の異なるバージョン間で <xref:System.Net.Mime.ContentDisposition.ToString%2A> メソッドの戻り値または <xref:System.Net.Mime.ContentDisposition> 日付と時刻のプロパティ値の文字列表現を比較する場合。|マイナー|  
  
<a name="WPF"></a>   
## Windows Presentation Foundation \(WPF\)  
  
|機能|変更|影響|スコープ|  
|--------|--------|--------|----------|  
|マルチ モニターのシナリオにおけるウィンドウのレンダリング|マルチ モニターのシナリオでディスプレイの外部にウィンドウを拡張すると、ウィンドウ全体がクリッピングなしでレンダリングされます。|「[軽減策: WPF ウィンドウのレンダリング](../../../docs/framework/migration-guide/mitigation-wpf-window-rendering.md)」を参照してください。|マイナー|  
|WPF テキスト対応コントロールのスペル チェック機能|プラットフォームのスペル チェック機能は入力言語リストに存在する言語でしか使用できないため、スペル チェック機能が Windows 10 での実行時に動作しないことがあります。|Windows 10 では、使用可能なキーボードのリストに言語を追加すると、対応するオンデマンド機能 \(FOD\) パッケージが自動的にダウンロードおよびインストールされ、スペル チェック機能が提供されます。 入力言語リストに言語を追加することで、スペル チェック機能がサポートされます。|マイナー|  
  
<a name="Setup"></a>   
## セットアップと配置  
  
|特性|変更|影響|スコープ|  
|--------|--------|--------|----------|  
|製品のバージョン管理|製品のバージョン管理が、.NET Framework の以前のリリース \(特に .NET Framework 4、4.5、4.5.1、および 4.5.2\) から変更されました。 詳細については、「[軽減策: 製品のバージョン管理](../../../docs/framework/migration-guide/mitigation-product-versioning.md)」を参照してください。|「[軽減策: 製品のバージョン管理](../../../docs/framework/migration-guide/mitigation-product-versioning.md)」を参照してください。|Medium|  
  
<a name="ClickOnce"></a>   
## ClickOnce  
  
|特性|変更|影響|スコープ|  
|--------|--------|--------|----------|  
|SHA\-256 コード署名証明書を使用して ClickOnce で発行されたアプリケーション。|[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 以前のバージョンをターゲットとし、SHA\-256 証明書で署名された ClickOnce アプリは、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降のバージョンに対するランタイム依存関係を持たなくなりました。|これまでは、SHA\-256 証明書を使用して [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 以前のバージョンをターゲットとする ClickOnce アプリは、ターゲット システム上に [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降のバージョンが存在しなければなりませんでした。 そのため、存在しない場合はエラーが発生しました。 この変更により、その依存関係がなくなったので、[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 以前のバージョンをターゲットとする ClickOnce アプリの署名にSAH\-256 証明書が使用できるようになりました。|マイナー|  
  
<a name="RyuJIT"></a>   
## 新しい 64 ビット JIT コンパイラ  
  
|特性|変更|影響|スコープ|  
|--------|--------|--------|----------|  
|例外処理 \(`try` 領域から返す\)|前の JIT64 just\-in\-time コンパイラとは異なり、新しい 64 ビット JIT コンパイラでは、`try` 領域での IL [ret](http://msdn.microsoft.com/library/system.reflection.emit.opcodes.ret.aspx) 命令は許可されません。|ECMA 335 仕様により `try` 領域から戻ることは許可されておらず、そうした IL を生成する既知のマネージ コンパイラはありません。 ただし、JIT64 コンパイラは、リフレクション出力を使用して生成される場合にはこうした IL を実行します。|エッジ|