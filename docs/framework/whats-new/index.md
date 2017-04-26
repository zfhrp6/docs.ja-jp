---
title: ".NET Framework の新機能 |Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework-4.6
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
caps.latest.revision: 292
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9460c8b6ca8db927af4064e3567eca34c1bf5c91
ms.openlocfilehash: 56bf5905fc9e4c676e2cf681c9135fddf88e5c89
ms.lasthandoff: 04/08/2017

---
# <a name="what39s-new-in-the-net-framework"></a>.NET Framework の新機能
<a name="introduction"></a> この記事では、.NET Framework の次のバージョンにおける主な新機能と機能強化の概要を示します。  
  
 [.NET Framework 4.7](#v47)   
 [.NET Framework 4.6.2](#v462)   
 [.NET Framework 4.6.1](#v461)   
 [.NET 2015 と .NET Framework 4.6](#v46)   
 [.NET Framework 4.5.2](#v452)   
 [.NET Framework 4.5.1](#v451)   
 [.NET Framework 4.5](#core)  
  
 この記事は、各新機能の包括的な情報を説明するものではありません。また、この内容は変更される可能性があります。 .NET Framework の概要については、「[.NET Framework の概要](http://msdn.microsoft.com/library/c693fd34-88fe-4d90-b332-19eeadf3b7e7)」をご覧ください。 サポートされているプラットフォームについては、「[.NET Framework システム要件](~/docs/framework/get-started/system-requirements.md)」を参照してください。 ダウンロード リンクとインストール手順については、「[.NET Framework のインストール](../../../docs/framework/install/guide-for-developers.md)」を参照してください。  
  
> [!NOTE]
>  また .NET Framework チームは、NuGet により OOB 機能をリリースすることによって、プラットフォーム サポートを拡張し、新しい機能 (変更できないコレクションや SIMD 対応ベクター型など) を提供しています。 詳細については、「[その他のクラス ライブラリと API](http://msdn.microsoft.com/library/cf2d9006-b631-4e5d-81cd-20aab78c60f1)」および[.NET Framework と OOB リリース](~/docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)に関するページを参照してください。 .NET Framework 用の [NuGet パッケージの完全な一覧](http://blogs.msdn.com/b/dotnet/p/nugetpackages.aspx)をご確認いただくか、[Microsoft のフィード](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/)をサブスクライブしてください。  
  
<a name="v47"></a>   
## <a name="introducing-the-net-framework-47"></a>.NET Framework 4.7 の概要  
 .NET Framework 4.7 は、.NET Framework 4.6、4.6.1、4.6.2 を基に、多数の新しい修正といくつかの新機能を追加したものであり、これまでと同様に非常に安定した製品です。  

> [!NOTE]
> .NET Framework 4.7 は、すべての Windows 10 Creators Update システムにプレインストールされています。 他の Windows オペレーティング システムにダウンロードまたはインストールすることはできません。  

## <a name="whats-new-in-the-net-framework-47"></a>.NET Framework 4.7 の新機能

.NET Framework 4.7 には、次の領域における新機能が含まれています。

- [コア](#Core47)
- [ネットワーク](#net47)
- [ASP.NET](#ASP-NET47)
- [Windows Communication Foundation (WCF)](#wcf47)
- [Windows フォーム](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

<a name="Core47" />
### <a name="core"></a>コア ###

.NET Framework 4.7 では、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> によるシリアル化が向上しています。

**楕円曲線暗号 (ECC) による機能強化***

.NET Framework 4.7 では `ImportParameters(ECParameters)` メソッドが <xref:System.Security.Cryptography.ECDsa> クラスと <xref:System.Security.Cryptography.ECDiffieHellman> クラスに追加され、既に確立されたキーをオブジェクトで表すことができるようになりました。 明示的な曲線パラメーターを使ってキーをエクスポートするための `ExportParameters(Boolean)` メソッドも追加されました。

また、.NET Framework 4.7 では、その他の曲線 (Brainpool 曲線スイートなど) のサポートと、新しい <xref:System.Security.Cryptography.ECDsa.Create%2A> および <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> ファクトリ メソッドによる作成しやすい事前定義も追加されています。

GitHub で [.NET Framework 4.7 の暗号化の向上の例](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e)を見ることができます。

**DataContractJsonSerializer による制御文字のサポートの向上**

.NET Framework 4.7 では、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は ECMAScript 6 標準に準拠して制御文字をシリアル化します。 この動作は、.NET Framework 4.7 を対象とするアプリケーションでは既定で有効になり、.NET Framework 4.7 で実行していても対象は以前のバージョンの .NET Framework であるアプリケーションの場合はオプトイン機能です。 詳細については、「[.NET Framework 4.7 における再ターゲットの変更点](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)」をご覧ください。

<a name="net47" />
### <a name="networking"></a>ネットワーク ###

.NET Framework 4.7 では、次のネットワーク関連機能が追加されています。

**TLS プロトコルの既定のオペレーティング システム サポート***

<xref:System.Net.Security.SslStream?displayProperty=fullName> および HTTP、FTP、SMTP などの上位スタック コンポーネントによって使われる TLS スタックにより、開発者はオペレーティング システムによってサポートされる既定の TLS プロトコルを使うことができます。 TLS バージョンをハード コーディングする必要はなくなりました。

<a name="ASP-NET47" />
### <a name="aspnet"></a>ASP.NET ###

.NET Framework 4.7 の ASP.NET には、次の新機能が含まれます。

**オブジェクト キャッシュの拡張性**

.NET Framework 4.7 以降では、ASP.NET で追加された新しい API セットを使うことで、開発者は、メモリ内オブジェクト キャッシュとメモリ監視に関する既定の ASP.NET の実装を置き換えることができます。 ASP.NET の実装が適切ではない場合、次の 3 つのコンポーネントを置き換えることができるようになりました。

- **オブジェクト キャッシュ ストア**。 新しいキャッシュ プロバイダー構成セクションを使うことで、開発者は、新しい **ICacheStoreProvider** インターフェイスを使って、ASP.NET アプリケーション用のオブジェクト キャッシュの新しい実装をプラグインできます。
 
- **メモリ監視**。 ASP.NET の既定のメモリ モニターは、アプリケーションがプロセスに構成されているプライベート バイト制限に近づくと、またはコンピューターの使用可能な合計物理 RAM が低下すると、アプリケーションに通知します。 これらの制限に近づくと、通知が発生します。 一部のアプリケーションでは、通知の発生が構成されている制限に近すぎるため、有効な対応を取れません。 .NET Framework 4.7 では、<xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=fullName> プロパティを使うことで、開発者が独自のメモリ モニターを作成して既定のモニターを置き換えることができます。

- **メモリ制限への対応**。 既定では、プライベート バイト プロセス制限が近づくと、ASP.NET はオブジェクト キャッシュの削減を試み、<xref:System.GC.Collect%2A?displayProperty=fullName> を定期的に呼び出します。 一部のアプリケーションでは、<xref:System.GC.Collect%2A?displayProperty=fullName> を呼び出す頻度または削減されるキャッシュの量が、十分ではありません。 開発者は、アプリケーションのメモリ モニターに **IObserver** の実装をサブスクライブすることにより、既定の動作を置換または補完できます。

<a name="wcf47" />
### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF) ###

Windows Communication Foundation (WFC) では以下の機能が追加または変更されました。

**既定のメッセージ セキュリティ設定を TLS1.1 または TLS1.2 に構成する機能。**

.NET Framework 4.7 以降の WCF では、既定のメッセージ セキュリティ プロトコルとして、SSL 3.0 と TSL 1.0 に加えて、TSL 1.1 または TLS 1.2 を構成できます。 これはオプトイン設定です。有効にするには、アプリケーション構成ファイルに次のエントリを追加する必要があります。

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" /> 
</runtime>
```

**WCF アプリケーションと WCF シリアル化の信頼性の向上**

WCF に競合状態を除去する複数のコード変更が追加され、シリアル化オプションの信頼性とパフォーマンスが向上しています。 次の設定があります。

- **SocketConnection.BeginRead** および **SocketConnection.Read** の呼び出しでの非同期コードと同期コードの併用のサポートの向上。
- **SharedConnectionListener** および **DuplexChannelBinder** で接続を中止するときの信頼性の向上。
- [FormatterServices.GetSerializableMembers](assetId:///System.Runtime.Serialization.FormatterServices.GetSerializableMembers(System.Type??qualifyHint=True&autoUpgrade=False) メソッドを呼び出すときのシリアル化操作の信頼性の向上。
- **ChannelSynchronizer.RemoveWaiter** メソッドを呼び出して待機を削除するときの信頼性の向上。  

<a name="wf47" />
### <a name="windows-forms"></a>Windows フォーム ###

.NET Framework 4.7 では、Windows フォームによる高 DPI モニターのサポートが向上しました。

**高 DPI のサポート**

.NET Framework 4.7 を対象とするアプリケーションでは、Windows フォーム アプリケーションに対して高 DPI および動的 DPI がサポートされるようになっています。 高 DPI のサポートにより、フォームのレイアウトと外観および高 DPI モニターでのコントロールが向上します。 動的 DPI は、ユーザーが実行中のアプリケーションの DPI または表示倍率を変更すると、フォームのレイアウトと外観およびコントロールを変更します。

高 DPI のサポートはオプトイン機能であり、アプリケーション構成ファイルの [\<System.Windows.Forms.ConfigurationSection>](Windows%20Forms%20Configuration%20Section.md) セクションを定義することで構成します。 Windows フォーム アプリケーションへの高 DPI サポートおよび動的 DPI サポート追加の詳細については、「[Windows フォームの高 DPI サポート](High%20DPI%20Support%20In%20Windows%20Forms.md)」をご覧ください。  

<a name="WPF47"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

.NET Framework 4.7 では、WPF の機能が次のように強化されています。

**Windows WM_POINTER メッセージに基づくタッチ/スタイラス スタックのサポート**

Windows Ink Services Platform (WISP) の代わりに [WM_POINTER メッセージ](https://msdn.microsoft.com/library/windows/desktop/hh454903(v=vs.85).aspx)に基づいてタッチ/スタイラス スタックを使うオプションが追加されました。 これは、.NET Framework のオプトイン機能です。 詳細については、「[.NET Framework 4.7 における再ターゲットの変更点](Retargeting%20Changes%20in%20the%20.NET%20Framework%204.7.md)」をご覧ください。

**WPF 印刷 API の新しい実装**

[System.Printing.PrintQueue](assetId:///T:System.Printing.PrintQueue?qualifyHint=True&autoUpgrade=True) クラスの WPF 印刷 API は、非推奨になった [XPS 印刷 API](https://msdn.microsoft.com/library/windows/desktop/ff686814(v=vs.85).aspx) ではなく Windows [ドキュメント印刷パッケージ API](https://msdn.microsoft.com/library/windows/desktop/hh448418(v=vs.85).aspx) を呼び出します。 アプリケーションの互換性に対するこの変更の影響については、「[.NET Framework 4.7 における再ターゲットの変更点](Retargeting%20Changes%20in%20the%20.NET%20Framework%204.7.md)」をご覧ください。 

<a name="v462"></a>   
## <a name="whats-new-in-the-net-framework-462"></a>.NET Framework 4.6.2 の新機能  
.NET Framework 4.6.2 には、次の領域における新機能が含まれています。  
  
-   [ASP.NET](#ASPNET462)  
  
-   [文字カテゴリ](#Strings)  
  
-   [暗号](#Crypto462)  
  
-   [SQLClient](#SQLClient)  
  
-   [Windows Communication Foundation](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF462)  
  
-   [Windows Workflow Foundation (WF)](#WF462)  
  
-   [ClickOnce](#ClickOnce)  
  
-   [Windows フォームおよび WPF アプリの UWP アプリへの変換](#UWPConvert)  
  
-   [デバッグの機能強化](#Debug462)  
  
 .NET Framework 4.6.2 に追加された新しい API の一覧については、GitHub で [.NET Framework 4.6.2 API の変更点](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md)に関するページを参照してください。 .NET Framework 4.6.2 における機能の改善とバグ修正の一覧については、GitHub で [.NET Framework 4.6.2 API の変更点](http://go.microsoft.com/fwlink/?LinkId=708778)に関するページを参照してください。  詳しくは、.NET Blog の「[Announcing .NET Framework 4.6.2](https://blogs.msdn.microsoft.com/dotnet/2016/08/02/announcing-net-framework-4-6-2/)」(.NET Framework 4.6.2 の発表) を参照してください。  
  
<a name="ASPNET462"></a>   
### <a name="aspnet"></a>ASP.NET  
 .NET Framework 4.6.2 では、ASP.NET の機能が次のように強化されています。  
  
 **データ注釈検証コントロールのローカライズされたエラー メッセージのサポート強化**  
 データ注釈検証コントロールを使用して、1 つ以上の属性をクラス プロパティに追加して検証を行うことができます。 属性の [ValidationAttribute.ErrorMessage](assetId:///P:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage?qualifyHint=True&autoUpgrade=True) 要素は、検証が失敗した場合にエラー メッセージのテキストを定義します。 .NET Framework 4.6.2 以降では、ASP.NET でエラー メッセージを簡単にローカライズできます。 エラー メッセージは次のような場合にローカライズされます。  
  
1.  [ValidationAttribute.ErrorMessage](assetId:///P:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage?qualifyHint=True&autoUpgrade=True) が検証属性で指定されている。  
  
2.  リソース ファイルが App_LocalResources フォルダーに格納されている。  
  
3.  ローカライズされたリソース ファイル名の形式が `DataAnnotation.Localization.{`*名前*`}.resx` (この*名前*は、*languageCode*`-`*country/regionCode* または *languageCode* 形式のカルチャ名) である。  
  
4.  リソースのキー名が [ValidationAttribute.ErrorMessage](assetId:///P:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage?qualifyHint=True&autoUpgrade=True) 属性に割り当てられている文字列で、その値がローカライズされたエラー メッセージである。  
  
 たとえば、次のデータ注釈属性では、無効な評価の場合に表示する、既定のカルチャのエラー メッセージを定義します。  
  
```csharp  
  
public class RatingInfo  
{  
   [Required(ErrorMessage = "The rating must be between 1 and 10.")]  
   [Display(Name = "Your Rating")]  
   public int Rating { get; set; }  
}  
  
```  
  
```vb  
  
Public Class RatingInfo  
   \<Required(ErrorMessage = "The rating must be between 1 and 10.")>  
   \<Display(Name = "Your Rating")>  
   Public Property Rating As Integer = 1  
End Class  
  
```  
  
 キーがエラー メッセージ文字列であり、その値がローカライズされたエラー メッセージであるようにリソース ファイル DataAnnotation.Localization.fr.resx を作成します。 ファイルは `App.LocalResources` フォルダーになければいけません。 たとえば下記は、キーとその値で、値はローカライズされたフランス語 (fr) のエラー メッセージです。  
  
|名前|値|  
|----------|-----------|  
|The rating must be between 1 and 10.|La note doit être comprise entre 1 et 10.|  
  
 This file can then  
  
 また、データ注釈ローカリゼーションを拡張することができます。 開発者は、[IStringLocalizerProvider](assetId:///T:System.Web.Globalization.IStringLocalizerProvider?qualifyHint=False&autoUpgrade=True) インターフェイスを実装してリソース ファイル以外の場所にローカリゼーション文字列を格納することで、独自の文字列ローカライザー プロバイダーにプラグインできます。  
  
 **セッション状態ストア プロバイダーでの非同期サポート**  
 ASP.NET では、セッション状態ストア プロバイダーでタスクを返すメソッドを使用できるようになりました。これにより、ASP.NET アプリで非同期のスケーラビリティのメリットが得られます。 セッション状態ストア プロバイダーでの非同期操作をサポートするために、ASP.NET には新しいインターフェイスである [System.Web.SessionState.ISessionStateModule](assetId:///T:System.Web.SessionState.ISessionStateModule?qualifyHint=True&autoUpgrade=True) が含まれています。これは [IHttpModule](assetId:///T:System.Web.IHttpModule?qualifyHint=False&autoUpgrade=True) から継承され、開発者はこれを使って独自のセッション状態モジュールと非同期セッション ストア プロバイダーを実装することができます。 このインターフェイスは次のように定義されます。  
  
```csharp  
  
public interface ISessionStateModule : IHttpModule {  
    void ReleaseSessionState(HttpContext context);  
    Task ReleaseSessionStateAsync(HttpContext context);  
}  
  
```  
  
 また、[SessionStateUtility](assetId:///T:System.Web.SessionState.SessionStateUtility?qualifyHint=False&autoUpgrade=True) クラスには [IsSessionStateReadOnly](assetId:///M:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly(System.Web.HttpContext)?qualifyHint=False&autoUpgrade=True) および [IsSessionStateRequired](assetId:///M:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired(System.Web.HttpContext)?qualifyHint=False&autoUpgrade=True) という 2 つの新しいメソッドが含まれています。これらを使って、非同期操作をサポートできます。  
  
 **出力キャッシュ プロバイダーの非同期サポート**  
 .NET Framework 4.6.2 以降では、タスクを返すメソッドを出力キャッシュ プロバイダーで使って、非同期のスケーラビリティのメリットを得ることができます。  これらのメソッドを実装するプロバイダーは、Web サーバー上のスレッド ブロックを減らし、ASP.NET サービスのスケーラビリティを向上させます。  
  
 非同期出力キャッシュ プロバイダーをサポートするために、次の API が追加されました。  
  
-   [System.Web.Caching.OutputCacheProviderAsync](assetId:///T:System.Web.Caching.OutputCacheProviderAsync?qualifyHint=True&autoUpgrade=True) クラス。これは [System.Web.Caching.OutputCacheProvider](assetId:///T:System.Web.Caching.OutputCacheProvider?qualifyHint=True&autoUpgrade=True) から継承され、開発者はこれを使って非同期出力キャッシュ プロバイダーを実装することができます。  
  
-   [OutputCacheUtility](assetId:///T:System.Web.Caching.OutputCacheUtility?qualifyHint=False&autoUpgrade=True) クラス。出力キャッシュを構成するためのヘルパー メソッドを提供します。  
  
-   [System.Web.HttpCachePolicy](assetId:///T:System.Web.HttpCachePolicy?qualifyHint=True&autoUpgrade=True) クラスの新しい 18 個のメソッド。 [GetCacheability](assetId:///M:System.Web.HttpCachePolicy.GetCacheability?qualifyHint=False&autoUpgrade=True)、[GetCacheExtensions](assetId:///M:System.Web.HttpCachePolicy.GetCacheExtensions?qualifyHint=False&autoUpgrade=True)、[GetETag](assetId:///M:System.Web.HttpCachePolicy.GetETag?qualifyHint=False&autoUpgrade=True)、[GetETagFromFileDependencies](assetId:///M:System.Web.HttpCachePolicy.GetETagFromFileDependencies?qualifyHint=False&autoUpgrade=True)、[GetMaxAge](assetId:///M:System.Web.HttpCachePolicy.GetMaxAge?qualifyHint=False&autoUpgrade=True)、[GetMaxAge](assetId:///M:System.Web.HttpCachePolicy.GetMaxAge?qualifyHint=False&autoUpgrade=True)、[GetNoStore](assetId:///M:System.Web.HttpCachePolicy.GetNoStore?qualifyHint=False&autoUpgrade=True)、[GetNoTransforms](assetId:///M:System.Web.HttpCachePolicy.GetNoTransforms?qualifyHint=False&autoUpgrade=True)、[GetOmitVaryStar](assetId:///M:System.Web.HttpCachePolicy.GetOmitVaryStar?qualifyHint=False&autoUpgrade=True)、[GetProxyMaxAge](assetId:///M:System.Web.HttpCachePolicy.GetProxyMaxAge?qualifyHint=False&autoUpgrade=True)、[GetRevalidation](assetId:///M:System.Web.HttpCachePolicy.GetRevalidation?qualifyHint=False&autoUpgrade=True)、[GetUtcLastModified](assetId:///M:System.Web.HttpCachePolicy.GetUtcLastModified?qualifyHint=False&autoUpgrade=True)、[GetVaryByCustom](assetId:///M:System.Web.HttpCachePolicy.GetVaryByCustom?qualifyHint=False&autoUpgrade=True)、[HasSlidingExpiration](assetId:///M:System.Web.HttpCachePolicy.HasSlidingExpiration?qualifyHint=False&autoUpgrade=True)、[IsValidUntilExpires](assetId:///M:System.Web.HttpCachePolicy.IsValidUntilExpires?qualifyHint=False&autoUpgrade=True)。  
  
-   [System.Web.HttpCacheVaryByContentEncodings](assetId:///T:System.Web.HttpCacheVaryByContentEncodings?qualifyHint=True&autoUpgrade=True) クラスの新しい 2 つのメソッド ([GetContentEncodings](assetId:///M:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings?qualifyHint=False&autoUpgrade=True) と [SetContentEncodings](assetId:///M:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings(System.String[])?qualifyHint=False&autoUpgrade=True))。  
  
-   [System.Web.HttpCacheVaryByHeaders](assetId:///T:System.Web.HttpCacheVaryByHeaders?qualifyHint=True&autoUpgrade=True) クラスの新しい 2 つのメソッド ([GetHeaders](assetId:///M:System.Web.HttpCacheVaryByHeaders.GetHeaders?qualifyHint=False&autoUpgrade=True) と [SetHeaders](assetId:///M:System.Web.HttpCacheVaryByHeaders.SetHeaders(System.String[])?qualifyHint=False&autoUpgrade=True))。  
  
-   [System.Web.HttpCacheVaryByParams](assetId:///T:System.Web.HttpCacheVaryByParams?qualifyHint=True&autoUpgrade=True) クラスの新しい 2 つのメソッド ([GetParams](assetId:///M:System.Web.HttpCacheVaryByParams.GetParams?qualifyHint=False&autoUpgrade=True) と [SetParams](assetId:///M:System.Web.HttpCacheVaryByParams.SetParams(System.String[])?qualifyHint=False&autoUpgrade=True))。  
  
-   [System.Web.Caching.AggregateCacheDependency](assetId:///T:System.Web.Caching.AggregateCacheDependency?qualifyHint=True&autoUpgrade=True) クラスの [GetFileDependencies](assetId:///M:System.Web.Caching.AggregateCacheDependency.GetFileDependencies?qualifyHint=False&autoUpgrade=True) メソッド。  
  
-   [CacheDependency](assetId:///T:System.Web.Caching.CacheDependency?qualifyHint=False&autoUpgrade=True) の [GetFileDependencies](assetId:///M:System.Web.Caching.CacheDependency.GetFileDependencies?qualifyHint=False&autoUpgrade=True) メソッド。  
  
<a name="Strings"></a>   
### <a name="character-categories"></a>文字カテゴリ  
 .NET Framework 4.6.2 の文字は [Unicode Standard バージョン 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/) に基づいて分類されます。 .NET Framework 4.6 と .NET Framework 4.6.1 では、文字は Unicode 6.3 文字のカテゴリに基づいて分類されました。  
  
 Unicode 8.0 のサポートは、[CharUnicodeInfo](assetId:///T:System.Globalization.CharUnicodeInfo?qualifyHint=False&autoUpgrade=True) クラスによる文字列の分類およびそれに依存する型とメソッドに限定されます。 これらには、[StringInfo](assetId:///T:System.Globalization.StringInfo?qualifyHint=False&autoUpgrade=True) クラス、オーバーロードされた [Char.GetUnicodeCategory](assetId:///M:System.Char.GetUnicodeCategory(System.Char)?qualifyHint=True&autoUpgrade=True) メソッド、および .NET Framework の正規表現エンジンによって認識される[文字クラス](../Topic/Character%20Classes%20in%20Regular%20Expressions.md)が含まれます。  文字や文字列の比較と並べ替えは、この変更の影響を受けることなく、引き続き基となるオペレーティング システムに依存します (Windows 7 システムの場合は、.NET Framework で提供される文字データに依存)。  
  
 Unicode 6.0 から Unicode 7.0 への文字カテゴリの変更については、Unicode Consortium Web サイトの [Unicode Standard バージョン 7.0.0](http://www.unicode.org/versions/Unicode7.0.0/) に関する記述を参照してください。 Unicode 7.0 から Unicode 8.0 への変更については、Unicode Consortium の Web サイトの [Unicode Standard バージョン 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/) に関する記述を参照してください。  
  
<a name="Crypto462"></a>   
### <a name="cryptography"></a>暗号  
 **FIPS 186-3 DSA を含む X509 証明書のサポート**  
 .NET Framework 4.6.2 には、FIPS 186-2 の 1024 ビットという制限を超えるキーを持つ、DSA (Digital Signature Algorithm) X509 証明書のサポートが追加されています。  
  
 より大きな FIPS 186-3 のキー サイズのサポートに加えて、.NET Framework 4.6.2 では、SHA-2 ファミリのハッシュ アルゴリズム (SHA256、SHA384、SHA512) によるシグネチャ計算も可能です。 FIPS 186-3 のサポートは、新しい [System.Security.Cryptography.DSACng](assetId:///T:System.Security.Cryptography.DSACng?qualifyHint=True&autoUpgrade=True) クラスによって提供されます。  
  
 .NET Framework 4.6 の [RSA](assetId:///T:System.Security.Cryptography.RSA?qualifyHint=False&autoUpgrade=True) クラスと .NET Framework 4.6.1 の [ECDsa](assetId:///T:System.Security.Cryptography.ECDsa?qualifyHint=False&autoUpgrade=True) クラスの最近の変更に合わせて、.NET Framework 4.6.2 の [DSA](assetId:///T:System.Security.Cryptography.DSA?qualifyHint=False&autoUpgrade=True) 抽象基底クラスにメソッドが追加されました。呼び出し元はこの機能をキャストせずに使うことができます。 データに署名する場合は、以下の例のように、[DSACertificateExtensions.GetDSAPrivateKey](assetId:///M:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?qualifyHint=True&autoUpgrade=True) 拡張メソッドを呼び出すことができます。  
  
```csharp  
  
public static byte[] SignDataDsaSha384(byte[] data, X509Certificate2 cert)  
{  
    using (DSA dsa = cert.GetDSAPrivateKey())  
    {  
        return dsa.SignData(data, HashAlgorithmName.SHA384);  
    }  
}  
  
```  
  
```vb  
  
Public Shared Function SignDataDsaSha384(data As Byte(), cert As X509Certificate2) As Byte()  
    Using DSA As DSA = cert.GetDSAPrivateKey()  
        Return DSA.SignData(data, HashAlgorithmName.SHA384)  
    End Using  
End Function  
  
```  
  
 署名データを検証する場合は、以下の例のように、[DSACertificateExtensions.GetDSAPublicKey](assetId:///M:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?qualifyHint=True&autoUpgrade=True) 拡張メソッドを呼び出すことができます。  
  
```csharp  
  
public static bool VerifyDataDsaSha384(byte[] data, byte[] signature, X509Certificate2 cert)  
{  
    using (DSA dsa = cert.GetDSAPublicKey())  
    {  
        return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384);  
    }  
}  
  
```  
  
```  
  
 Public Shared Function VerifyDataDsaSha384(data As Byte(), signature As Byte(), cert As X509Certificate2) As Boolean  
    Using dsa As DSA = cert.GetDSAPublicKey()  
        Return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384)  
    End Using  
End Function  
  
```  
  
 **ECDiffieHellman キー派生ルーチンへの入力をよりわかりやすく**  
 .NET Framework 3.5 では、3 種類の KDF (キー派生関数) ルーチンによる Elliptic Curve Diffie-Hellman キー承諾のサポートが追加されました。 ルーチンへの入力、およびルーチン自体は [ECDiffieHellmanCng](assetId:///T:System.Security.Cryptography.ECDiffieHellmanCng?qualifyHint=False&autoUpgrade=True) オブジェクトのプロパティで構成されました。 しかし、すべてのルーチンですべての入力プロパティが読み取られるわけではないため、これまで開発者がよく混乱することがありました。  
  
 .NET Framework 4.6.2 ではこれに対処するために、次の 3 つのメソッドが [ECDiffieHellman](assetId:///T:System.Security.Cryptography.ECDiffieHellman?qualifyHint=False&autoUpgrade=True) 基底クラスに追加され、これらの KDF ルーチンとその入力がよりわかりやくなりました。  
  
|ECDiffieHellman メソッド|説明|  
|----------------------------|-----------------|  
|[DeriveKeyFromHash(ECDiffieHellmanPublicKey, HashAlgorithmName, Byte\[\], Byte\[\])](assetId:///M:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash(System.Security.Cryptography.ECDiffieHellmanPublicKey,System.Security.Cryptography.HashAlgorithmName,System.Byte[],System.Byte[])?qualifyHint=False&autoUpgrade=False)|次の式を使用してキー マテリアルを派生させます。<br /><br /> HASH(secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HASH(secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> ここで *x* は、EC Diffie-Hellman アルゴリズムの計算結果を表します。|  
|[DeriveKeyFromHmac(ECDiffieHellmanPublicKey, HashAlgorithmName, Byte\[\], Byte\[\], Byte\[\])](assetId:///M:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac(System.Security.Cryptography.ECDiffieHellmanPublicKey,System.Security.Cryptography.HashAlgorithmName,System.Byte[],System.Byte[],System.Byte[])?qualifyHint=False&autoUpgrade=False)|次の式を使用してキー マテリアルを派生させます。<br /><br /> HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> ここで *x* は、EC Diffie-Hellman アルゴリズムの計算結果を表します。|  
|[DeriveKeyTls(ECDiffieHellmanPublicKey, Byte\[\], Byte\[\])](assetId:///M:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls(System.Security.Cryptography.ECDiffieHellmanPublicKey,System.Byte[],System.Byte[])?qualifyHint=False&autoUpgrade=False)|TLS 擬似乱数関数 (PRF) 派生アルゴリズムを使用して、キー マテリアルを派生させます。|  
  
 **永続化されたキーによる対称暗号化のサポート**  
 Windows の暗号化ライブラリ (CNG) では、永続化された対称キーの格納とハードウェアに格納された対称キーの使用のサポートが追加され、.NET Framework 4.6.2 で開発者はこの機能を利用できるようになりました。  キー名とキー プロバイダーの概念が実装に固有であるため、この機能を使用するには、推奨されるファクトリ手法 (`Aes.Create` の呼び出しなど) ではなく、具象実装型のコンストラクターを利用する必要があります。  
  
 永続化されたキーによる対称暗号化は、AES ([AesCng](assetId:///T:System.Security.Cryptography.AesCng?qualifyHint=False&autoUpgrade=True)) と 3DES ([TripleDESCng](assetId:///T:System.Security.Cryptography.TripleDESCng?qualifyHint=False&autoUpgrade=True)) アルゴリズムでサポートされます。 例:  
  
```csharp  
  
public static byte[] EncryptDataWithPersistedKey(byte[] data, byte[] iv)  
{  
    using (Aes aes = new AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider))  
    {  
        aes.IV = iv;  
  
        // Using the zero-argument overload is required to make use of the persisted key  
        using (ICryptoTransform encryptor = aes.CreateEncryptor())  
        {  
            if (!encryptor.CanTransformMultipleBlocks)  
            {  
                throw new InvalidOperationException("This is a sample, this case wasn’t handled...");  
            }  
  
            return encryptor.TransformFinalBlock(data, 0, data.Length);  
        }  
    }  
}  
  
```  
  
```vb  
  
Public Shared Function EncryptDataWithPersistedKey(data As Byte(), iv As Byte()) As Byte()  
    Using Aes As Aes = New AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider)  
        Aes.IV = iv  
  
        ' Using the zero-argument overload Is required to make use of the persisted key  
        Using encryptor As ICryptoTransform = Aes.CreateEncryptor()  
            If Not encryptor.CanTransformMultipleBlocks Then  
                Throw New InvalidOperationException("This is a sample, this case wasn’t handled...")  
            End If  
            Return encryptor.TransformFinalBlock(data, 0, data.Length)  
        End Using  
    End Using  
End Function  
  
```  
  
 **SHA-2 ハッシュの SignedXml サポート**  
 .NET Framework 4.6.2 では [SignedXml](assetId:///T:System.Security.Cryptography.Xml.SignedXml?qualifyHint=False&autoUpgrade=True) クラスに対するサポートが追加され、RSA-SHA256、RSA-SHA384、RSA-SHA512 の各 PKCS#1 署名メソッド、および SHA256、SHA384、SHA512 の各参照ダイジェスト アルゴリズムが使うことができるようになりました。  
  
 以下のように、URI 定数はすべて [SignedXml](xref:System.Security.Cryptography.Xml.SignedXml?qualifyHint=False&autoUpgrade=True) で示されます。  
  
|SignedXml フィールド|定数|  
|---------------------|--------------|  
|[XmlDsigSHA256Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmlenc#sha256"|  
|[XmlDsigRSASHA256Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|  
|[XmlDsigSHA384Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmldsig-more#sha384"|  
|[XmlDsigRSASHA384Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|  
|[XmlDsigSHA512Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmlenc#sha512"|  
|[XmlDsigRSASHA512Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|  
  
 これらのアルゴリズムのサポートを追加するためにカスタム [SignatureDescription](assetId:///T:System.Security.Cryptography.SignatureDescription?qualifyHint=False&autoUpgrade=True) ハンドラーを [CryptoConfig](assetId:///T:System.Security.Cryptography.CryptoConfig?qualifyHint=False&autoUpgrade=True) に登録していたプログラムはすべて従来どおり引き続き機能しますが、既定でプラットフォームでサポートされるようになったため、[CryptoConfig](assetId:///T:System.Security.Cryptography.CryptoConfig?qualifyHint=False&autoUpgrade=True) への登録は不要になりました。  
  
<a name="SQLClient"></a>   
### <a name="sqlclient"></a>SqlClient  
 .NET Framework SQL Server 用データ プロバイダー ([System.Data.SqlClient](assetId:///N:System.Data.SqlClient?qualifyHint=True&autoUpgrade=True)) には、.NET Framework 4.6.2 の次の新機能が含まれています。  
  
 **Azure SQL Database への接続プールとタイムアウト**  
 接続プールが有効な状態で、タイムアウトまたは他のログイン エラーが発生した場合は、例外がキャッシュされ、キャッシュされた例外は次の 5 秒から 1 分の間の後続の接続試行時にすべてスローされます。  詳細については、「[SQL Server の接続プール (ADO.NET)](../Topic/SQL%20Server%20Connection%20Pooling%20\(ADO.NET\).md)」を参照してください。  
  
 通常は迅速に復旧される一時的なエラーで接続試行が失敗する可能性があるため、Azure SQL Database への接続時のこの動作は望ましくありません。 接続試行操作をより最適化するため、Azure SQL Database への接続が失敗した場合は、接続プールのブロック期間の動作は削除されます。  
  
 新しい `PoolBlockingPeriod` キーワードを追加することで、使用しているアプリに最適なブロック期間を選択できます。 次の値が含まれます。  
  
 `Auto`  
 Azure SQL Database に接続しているアプリケーションの接続プールのブロック期間は無効になり、他のすべての SQL Server インスタンスに接続しているアプリケーションの接続プールのブロック期間が有効になります。 これが既定値です。 サーバー エンドポイント名の末尾が以下のいずれかである場合は、Azure SQL Database と見なされます。  
  
-   .database.windows.net  
  
-   .database.chinacloudapi.cn  
  
-   .database.usgovcloudapi.net  
  
-   .database.cloudapi.de  
  
 `AlwaysBlock`  
 接続プールのブロック期間は常に有効になります。  
  
 `NeverBlock`  
 接続プールのブロック期間は常に無効になります。  
  
 **Always Encrypted の強化**  
 SQLClient では、Always Encrypted の以下の 2 つの機能が強化されました。  
  
-   暗号化されたデータベースの列に対するパラメーター クエリのパフォーマンスを向上させるために、クエリ パラメーターの暗号化メタデータがキャッシュされるようになりました。 [SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled](assetId:///P:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled?qualifyHint=True&autoUpgrade=True) プロパティを `true` (既定値) に設定した状態で、同じクエリが複数回呼び出されると、クライアントはパラメーターのメタデータをサーバーから 1 回だけ取得します。  
  
-   キー キャッシュ内の列暗号化キー エントリは、[SqlConnection.ColumnEncryptionKeyCacheTtl](assetId:///P:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl?qualifyHint=True&autoUpgrade=True) プロパティを使って設定された構成可能な時間間隔後に削除されるようになりました。  
  
<a name="WCF"></a>   
### <a name="windows-communication-foundation"></a>Windows Communication Foundation  
 .NET Framework 4.6.2 では、Windows Communication Foundation の次の領域の機能が強化されています。  
  
 **CNG を使用して格納される証明書の WCF トランスポート セキュリティ サポート**  
 WCF トランスポート セキュリティでは、Windows 暗号化ライブラリ (CNG) を使用して格納される証明書がサポートされます。 .NET Framework 4.6.2 では、このサポートは、指数の長さが 32 ビット以下の公開キーを持つ証明書を使う場合に限定されます。 .NET Framework 4.6.2 を対象とするアプリケーションでは、この機能は既定で有効になります。  
  
 .NET Framework 4.6.1 以前を対象とするアプリケーションが .NET Framework 4.6.2 以降で実行されている場合、app.config または web.config ファイルの [\<runtime>](../Topic/%3Cruntime%3E%20Element.md) セクションに次の行を追加することで、この機能を有効にできます。  
  
```xml  
  
<AppContextSwitchOverrides  
    value="Switch.System.ServiceModel.DisableCngCertificates=false"  
/>  
  
```  
  
 以下のようなコードを使用してプログラムで行うこともできます。  
  
```csharp  
  
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";  
AppContext.SetSwitch(disableCngCertificates, false);  
  
```  
  
```vb  
  
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"  
AppContext.SetSwitch(disableCngCertificates, False)  
  
```  
  
 **DataContractJsonSerializer クラスによる複数の夏時間調整規則のサポート強化**  
 お客様はアプリケーションの構成設定を使って、[DataContractJsonSerializer](assetId:///T:System.Runtime.Serialization.Json.DataContractJsonSerializer?qualifyHint=False&autoUpgrade=True) クラスで 1 つのタイム ゾーンに対して複数の調整規則がサポートされているかどうかを判別することができます。 これはオプトイン機能です。 これを有効にするには、app.config ファイルに次の設定を追加します。  
  
```xml  
  
<runtime>  
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />  
</runtime>  
  
```  
  
 この機能を有効にすると、[DataContractJsonSerializer](assetId:///T:System.Runtime.Serialization.Json.DataContractJsonSerializer?qualifyHint=False&autoUpgrade=True) オブジェクトが [TimeZone](assetId:///T:System.TimeZone?qualifyHint=False&autoUpgrade=True) 型の代わりに [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) 型を使って、日付と時刻のデータを逆シリアル化します。 [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) では、[TimeZone](assetId:///T:System.TimeZone?qualifyHint=False&autoUpgrade=True) でサポートされない複数の調整規則がサポートされるため、過去のタイム ゾーン データを操作できます。  
  
 [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) 構造体とタイム ゾーン調整の詳細については、「[タイム ゾーンの概要](../Topic/Time%20Zone%20Overview.md)」を参照してください。  
  
 **XMLSerializer クラスでのシリアル化と逆シリアル化の際に UTC 時刻を保持するサポート**  
 通常、[XmlSerializer](assetId:///T:System.Xml.Serialization.XmlSerializer?qualifyHint=False&autoUpgrade=True) クラスを使用して UTC の [DateTime](assetId:///T:System.DateTime?qualifyHint=False&autoUpgrade=True) 値をシリアル化する場合、日時は保持するものの、現地時刻と見なすシリアル化された時刻文字列が作成されます。  たとえば、次のコードを呼び出して UTC 日時をインスタンス化するとします。  
  
```csharp  
DateTime utc = new DateTime(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc);  
```  
  
```vb  
Dim utc As New Date(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc)  
```  
  
 この場合、システムのシリアル化された時刻文字列は、UTC より 8 時間遅れの "03:00:00.0000000-08:00" となります。  シリアル化された値は常に、現地日時の値として逆シリアル化されます。  
  
 アプリケーションの構成設定を使用すれば、[DateTime](assetId:///T:System.DateTime?qualifyHint=False&autoUpgrade=True) 値のシリアル化と逆シリアル化のときに [XmlSerializer](assetId:///T:System.Xml.Serialization.XmlSerializer?qualifyHint=False&autoUpgrade=True) で UTC タイム ゾーンの情報が保持されるかどうかを判別できます。  
  
```xml  
  
<runtime>  
     <AppContextSwitchOverrides   
          value="Switch.System.Runtime.Serialization.DisableSerializeUTCDateTimeToTimeAndDeserializeUTCTimeToUTCDateTime=false" />  
</runtime>  
  
```  
  
 この機能を有効にすると、[DataContractJsonSerializer](assetId:///T:System.Runtime.Serialization.Json.DataContractJsonSerializer?qualifyHint=False&autoUpgrade=True) オブジェクトが [TimeZone](assetId:///T:System.TimeZone?qualifyHint=False&autoUpgrade=True) 型の代わりに [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) 型を使って、日付と時刻のデータを逆シリアル化します。 [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) では、[TimeZone](assetId:///T:System.TimeZone?qualifyHint=False&autoUpgrade=True) でサポートされない複数の調整規則がサポートされるため、過去のタイム ゾーン データを操作できます。  
  
 [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) 構造体とタイム ゾーン調整の詳細については、「[タイム ゾーンの概要](../Topic/Time%20Zone%20Overview.md)」を参照してください。  
  
 **NetNamedPipeBinding の最適な一致**  
 WCF には、クライアント アプリケーションで設定できる新しいアプリ設定があります。これにより、クライアント アプリケーションは常に、要求したものと最も一致する URI でリッスンしているサービスに接続できます。 このアプリ設定が `false` (既定値) に設定されている場合、クライアントは [NetNamedPipeBinding](assetId:///T:System.ServiceModel.NetNamedPipeBinding?qualifyHint=False&autoUpgrade=True) を使って、要求した URI の部分文字列である URI でリッスンしているサービスへの接続を試行できます。  
  
 たとえば、クライアントが `net.pipe://localhost/Service1` でリッスンしているサービスに接続しようとしているときに、管理者特権で実行しているコンピューター上の別のサービスが `net.pipe://localhost` でリッスンしているとします。 このアプリ設定が `false` に設定されている場合、クライアントは間違ったサービスに接続しようとします。 アプリ設定を `true` に設定すれば、クライアントは常に最も一致するサービスに接続するようになります。  
  
> [!NOTE]
>  [NetNamedPipeBinding](assetId:///T:System.ServiceModel.NetNamedPipeBinding?qualifyHint=False&autoUpgrade=True) を使うクライアントは、完全なエンドポイント アドレスではなく、サービスのベース アドレス (存在する場合) に基づいてサービスを検索します。 この設定が常に機能するようにするには、サービスは一意のベース アドレスを使用する必要があります。  
  
 この変更を有効にするには、以下のアプリ設定をクライアント アプリケーションの App.config ファイルまたは Web.config ファイルに追加します。  
  
```xml  
  
<configuration>  
    <appSettings>  
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />  
    </appSettings>  
</configuration>  
  
```  
  
 **SSL 3.0 が既定のプロトコルではなくなった**  
 トランスポート セキュリティで NetTcp を使用し、証明書の資格情報の種類を使用する場合、SSL 3.0 は、安全な接続のネゴシエーションに使用される既定のプロトコルではなくなりました。 TLS 1.0 が NetTcp のプロトコル一覧に含まれているため、ほとんどの場合、既存のアプリには影響はないと考えられます。 既存のすべてのクライアントは TLS 1.0 以降を使用して接続をネゴシエートできるようになりました。      Ssl3 が必要な場合は、以下の構成メカニズムのいずれかを使用して、ネゴシエートされたプロトコルの一覧に追加します。  
  
-   [SslStreamSecurityBindingElement.SslProtocols](assetId:///P:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?qualifyHint=True&autoUpgrade=True) プロパティ  
  
-   [TcpTransportSecurity.SslProtocols](assetId:///P:System.ServiceModel.TcpTransportSecurity.SslProtocols?qualifyHint=True&autoUpgrade=True) プロパティ  
  
-   [\<netTcpBinding>](../Topic/%3CnetTcpBinding%3E.md) セクションの [\<transport>](../Topic/%3Ctransport%3E%20of%20%3CnetTcpBinding%3E.md) セクション  
  
-   [\<customBinding>](../Topic/%3CcustomBinding%3E.md) セクションの [\<sslStreamSecurity>](../Topic/%3CsslStreamSecurity%3E.md) セクション  
  
<a name="WPF462"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 .NET Framework 4.6.2 では、Windows Presentation Foundation の次の領域の機能が強化されています。  
  
 **グループの並べ替え**  
 [CollectionView](assetId:///T:System.Windows.Data.CollectionView?qualifyHint=False&autoUpgrade=True) オブジェクトを使ってデータをグループ化するアプリケーションは、グループを並べ替える方法を明示的に宣言できるようになりました。 明示的な並べ替えにより、アプリがグループを動的に追加または削除する場合や、グループ化に関連する項目のプロパティの値を変更する場合に発生する非直感的な順序付けの問題が解決されます。 また、グループ化プロパティの比較がコレクション全体の並べ替えからグループの並べ替えに変更されるため、グループ作成プロセスのパフォーマンスを向上させることができます。  
  
 グループの並べ替えをサポートするために、新しい [GroupDescription.SortDescriptions](assetId:///P:System.ComponentModel.GroupDescription.SortDescriptions?qualifyHint=True&autoUpgrade=True) および [GroupDescription.CustomSort](assetId:///P:System.ComponentModel.GroupDescription.CustomSort?qualifyHint=True&autoUpgrade=True) プロパティで、[GroupDescription](assetId:///T:System.ComponentModel.GroupDescription?qualifyHint=False&autoUpgrade=True) オブジェクトによって生成されるグループのコレクションを並べ替える方法が示されます。 これは、同じ名前の [ListCollectionView](assetId:///T:System.Windows.Data.ListCollectionView?qualifyHint=False&autoUpgrade=True) プロパティでデータ項目を並べ替える方法を示すのと同様です。  
  
 [PropertyGroupDescription](assetId:///T:System.Windows.Data.PropertyGroupDescription?qualifyHint=False&autoUpgrade=True) クラスの新しい 2 つの静的プロパティである [CompareNameAscending](assetId:///P:System.Windows.Data.PropertyGroupDescription.CompareNameAscending?qualifyHint=False&autoUpgrade=True) と [CompareNameDescending](assetId:///P:System.Windows.Data.PropertyGroupDescription.CompareNameDescending?qualifyHint=False&autoUpgrade=True) は、最も一般的なケースで使うことができます。  
  
 たとえば、次の XAML ではデータを年齢でグループ化し、年齢グループを昇順に並べ替え、各年齢グループ内の項目を姓でグループ化します。  
  
```xaml  
  
<GroupDescriptions>  
     \<PropertyGroupDescription   
         PropertyName=”Age”   
         CustomSort=   
              ”{x:Static PropertyGroupDescription.CompareNamesAscending}”/>  
     </PropertyGroupDescription>  
</GroupDescriptions>  
  
<SortDescriptions>  
     \<SortDescription PropertyName=”LastName”/>  
</SortDescriptions>  
  
```  
  
 **ソフト キーボードのサポート**  
 ソフト キーボードのサポートにより、WPF アプリケーションでのフォーカス追跡が可能になります。テキスト入力が可能なコントロールによりタッチ入力を受信すると、Windows 10 の新しいソフト キーボードが自動的に起動および終了します。  
  
 .NET Framework の以前のバージョンでは、WPF アプリケーションは、WPF のペン/タッチ ジェスチャ サポートを無効にしないとフォーカス追跡を選択できません。  そのため、WPF アプリケーションは完全な WPF タッチのフル サポートを選ぶか、Windows のマウス プロモーションに依存する必要があります。  
  
 **モニターごとの DPI**  
 WPF アプリ用の高 DPI とハイブリッド DPI 環境の最近の急激な増加に対応するために、.NET Framework 4.6.2 の WPF でモニターごとに対応できるようになりました。 ご使用の WPF アプリでモニターごとの DPI 対応を有効にする方法の詳細については、GitHub の[サンプルと開発者向けガイド](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI)に関するページを参照してください。  
  
 .NET Framework の以前のバージョンでは、WPF アプリはシステム DPI 対応です。 つまり、アプリケーションの UI は、アプリがレンダリングされるモニターの DPI に基づき、必要に応じて OS でスケーリングされます。 ,  
  
 .NET Framework 4.6.2 で実行されるアプリの場合、次のように、アプリケーションの構成ファイルの [\<runtime>](../Topic/%3Cruntime%3E%20Element.md) セクションに構成ステートメントを追加して、WPF アプリでモニターごとの DPI 変更を無効にすることができます。  
  
```xml  
  
<runtime>  
   \<AppContextSwitchOverrides value=”Switch.System.Windows.DoNotScaleForDpiChanges=false”/>  
</runtime>  
  
```  
  
<a name="WF462"></a>   
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)  
 .NET Framework 4.6.2 では、Windows Workflow Foundation の次領域の機能が強化されています。  
  
 **再ホストされた WF デザイナーにおける C# 式と IntelliSense のサポート**  
 .NET Framework 4.5 以降では、WF によって、Visual Studio デザイナーとコード ワークフローの両方で C# 式がサポートされます。 再ホストされたワークフロー デザイナーは WF の主な機能です。これにより、ワークフロー デザイナーを Visual Studio の外部のアプリケーション (WPF など) で使用できるようになります。  Windows Workflow Foundation は、再ホストされたワークフロー デザイナーで C# 式と IntelliSense をサポートできるようにします。 詳細については、[Windows Workflow Foundation のブログ](http://go.microsoft.com/fwlink/?LinkID=809042&clcid=0x409)を参照してください。  
  
 `Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`  
 .NET Framework 4.6.2 より前のバージョンの .NET Framework で、お客様が Visual Studio からワークフロー プロジェクトを再ビルドした場合、WF Designer IntelliSense は破損してしまいます。 プロジェクトのビルドに成功しても、デザイナーでワークフローの種類が見つからず、**[エラー一覧]** ウィンドウにワークフローの種類が欠落していることを示す IntelliSense からの警告が表示されます。 .NET Framework 4.6.2 はこの問題に対処し、IntelliSense を使うことができるようにします。  
  
 **ワークフロー追跡を有効にしたワークフロー V1 アプリケーションを FIPS モードで実行**  
 FIPS コンプライアンス モードが有効なコンピューターで、ワークフロー追跡が有効なワークフロー バージョン 1 スタイルのアプリケーションを正常に実行できるようになりました。 このシナリオを有効にするには、app.config ファイルを以下のように変更する必要があります。  
  
```xml  
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />  
```  
  
 このシナリオが有効でない場合、アプリケーションを実行すると、引き続き例外が生成され、"この実装は Windows プラットフォーム FIPS 検証暗号化アルゴリズムの一部ではありません" というメッセージが表示されます。  
  
 **Visual Studio ワークフロー デザイナーで動的更新を使用する場合のワークフローの改善**  
 ワークフロー デザイナー、フローチャート アクティビティ デザイナー、およびその他のワークフロー アクティビティ デザイナーで、[DynamicUpdateServices.PrepareForUpdate](assetId:///M:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate(System.Activities.Activity)?qualifyHint=True&autoUpgrade=True) メソッドを呼び出した後に保存されたワークフローが正常に読み込まれ、表示されるようになりました。 .NET Framework 4.6.2 より前のバージョンの .NET Framework では、[DynamicUpdateServices.PrepareForUpdate](assetId:///M:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate(System.Activities.Activity)?qualifyHint=True&autoUpgrade=True) を呼び出した後に保存されたワークフローの XAML ファイルを Visual Studio で読み込むと、以下の問題が発生する場合がありました。  
  
-   ワークフロー デザイナーで XAML ファイルが正しく読み込めない (行の末尾に [ViewStateData.Id](assetId:///P:System.Activities.Presentation.ViewState.ViewStateData.Id?qualifyHint=True&autoUpgrade=True) がある場合)。  
  
-   フローチャート アクティビティ デザイナーまたは他のワークフロー アクティビティ デザイナーで、アタッチされるプロパティの値ではなく既定の場所にすべてのオブジェクトが表示される場合がある。  
  
<a name="ClickOnce"></a>   
### <a name="clickonce"></a>ClickOnce  
 ClickOnce が更新され、既にサポートされている 1.0 プロトコルに加え、TLS 1.1 と TLS 1.2 がサポートがサポートされるようになりました。 ClickOnce が必要なプロトコルを自動的に検出するため、TLS 1.1 と 1.2 のサポートを有効にするために、ClickOnce アプリケーション内での追加の手順は不要です。  
  
<a name="UWPConvert"></a>   
### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Windows フォームおよび WPF アプリの UWP アプリへの変換  
 Windows では、WPF および Windows フォーム アプリを含む、既存の Windows デスクトップ アプリを UWP (ユニバーサル Windows プラットフォーム) で使用できるようになりました。 このテクノロジはブリッジとして機能し、既存のコード ベースを段階的に UWP に移行し、アプリをすべての Windows 10 デバイスで使用できるようにします。  
  
 変換後のデスクトップ アプリは UWP アプリのアプリ ID のようなアプリ ID を取得し、UWP API をアクセス可能にして、ライブ タイルや通知などの機能を有効にすることができます。 アプリは引き続き従来どおり動作し、完全信頼アプリとして実行されます。 アプリが変換されたら、アプリ コンテナー プロセスを既存の完全信頼プロセスに追加し、適応ユーザー インターフェイスを追加できます。 すべての機能がアプリ コンテナー プロセスに移行されたら、完全信頼プロセスを削除し、新しい UWP アプリをすべての Windows 10 デバイスで有効にすることができます。  
  
<a name="Debug462"></a>   
### <a name="debugging-improvements"></a>デバッグの機能強化  
 .NET Framework 4.6.2 で*アンマネージ デバッグ API* が強化され、[NullReferenceException](assetId:///T:System.NullReferenceException?qualifyHint=False&autoUpgrade=True) がスローされたときに追加分析を実行し、ソース コードの単一行でどの変数が `null` になっているかを判別できるようになりました。   このシナリオをサポートするために、次の API がアンマネージ デバッグ API に追加されました。  
  
-   [ICorDebugCode4](../Topic/ICorDebugCode4%20Interface.md)、[ICorDebugVariableHome](../Topic/ICorDebugVariableHome%20Interface.md)、および [ICorDebugVariableHomeEnum](../Topic/ICorDebugVariableHomeEnum%20Interface.md) インターフェイス。これらは管理対象変数の元のホームを公開します。 これにより、デバッガーは、[NullReferenceException](assetId:///T:System.NullReferenceException?qualifyHint=False&autoUpgrade=True) の発生時になんらかのコード フロー分析を行い、さかのぼって、`null` だった元の場所に対応する管理対象変数を判別できます。  
  
-   [ICorDebugType2::GetTypeID](../Topic/ICorDebugType2::GetTypeID%20Method.md) メソッドでは ICorDebugType を [COR_TYPEID](../Topic/COR_TYPEID%20Structure.md) にマッピングできます。これにより、デバッガーは、ICorDebugType のインスタンスがなくても [COR_TYPEID](../Topic/COR_TYPEID%20Structure.md) を取得できます。 その後、[COR_TYPEID](../Topic/COR_TYPEID%20Structure.md) で既存の API を使用して、型のクラス レイアウトを判別できます。  
  
<a name="v461"></a>   
## <a name="whats-new-in-the-net-framework-461"></a>.NET Framework 4.6.1 の新機能  
 .NET Framework 4.6.1 には、次の領域における新機能が含まれています。  
  
-   [暗号](#Crypto)  
  
-   [ADO.NET](#ADO.NET461)  
  
-   [Windows Presentation Foundation (WPF)](#WPF461)  
  
-   [Windows Workflow Foundation](#WWF461)  
  
-   [プロファイル](#Profile461)  
  
-   [NGen](#NGEN461)  
  
 .NET Framework 4.6.1 の詳細については、次のトピックを参照してください。  
  
-   [.NET Framework 4.6.1 の変更の一覧](http://go.microsoft.com/fwlink/?LinkId=622964)  
  
-   [4.6.1 のアプリケーションの互換性](../Topic/Application%20Compatibility%20in%20the%20.NET%20Framework%204.6.1.md)  
  
-   [.NET Framework API の diff (差分)](http://go.microsoft.com/fwlink/?LinkId=622989) (GitHub 上)  
  
<a name="Crypto"></a>   
### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>暗号化: ECDSA を含む X509 証明書のサポート  
 .NET Framework 4.6 では、X509 証明書の RSACng サポートが追加されました。 .NET Framework 4.6.1 では、ECDSA (Elliptic Curve Digital Signature Algorithm: 楕円曲線デジタル署名アルゴリズム) X509 証明書のサポートが追加されました。  
  
 ECDSA は、RSA よりも安全な暗号化アルゴリズムで、パフォーマンスも向上するため、トランスポート層セキュリティ (TLS) のパフォーマンスとスケーラビリティが問題になる場合に最適な選択肢です。 .NET Framework の実装では、既存の Windows 機能の呼び出しがラップされます。  
  
 次のサンプル コードでは、.NET Framework 4.6.1 での新しい ECDSA X509 証明書のサポートを使ってバイト ストリームの署名が簡単に生成できることを示しています。  
  
<!-- TODO: review snippet reference  [!CODE [whatsnew.461.crypto#1](../CodeSnippet/VS_Snippets_CLR/whatsnew.461.crypto#1)]  -->  
  
 このコードは、.NET Framework 4.6 での署名の生成に必要な次のコードとは大きく異なっています。  
  
<!-- TODO: review snippet reference  [!CODE [whatsnew.461.crypto#2](../CodeSnippet/VS_Snippets_CLR/whatsnew.461.crypto#2)]  -->  
  
<a name="ADO.NET461"></a>   
### ADO.NET 次のものが ADO.NET に追加されました。  
  
 ハードウェア保護キーに対する Always Encrypted のサポート  
 ADO.NET では、Always Encrypted 列 (常に暗号化される列) のマスター キーをハードウェア セキュリティ モジュール (HSM) に格納することが、ネイティブでサポートされるようになりました。 このサポートによって、ユーザーは、HSM に格納された非対称キーを利用できます。カスタムの列マスター キー ストア プロバイダーを作成してからアプリケーションに登録する必要はありません。  
  
 HSM に格納された列マスター キーで保護された Always Encrypted データにアクセスするには、HSM ベンダー提供の CSP プロバイダーまたは CNG キー ストア プロバイダーをアプリ サーバーまたはクライアント コンピューターにインストールする必要があります。  
  
 AlwaysOn に対する [MultiSubnetFailover](assetId:///P:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover?qualifyHint=False&autoUpgrade=True) の接続動作の向上  
 SqlClient で、AlwaysOn 可用性グループ (AG) へのより高速な接続が自動的に提供されるようになりました。 SqlClient では、アプリケーションが別のサブネット上の AlwaysOn 可用性グループ (AG) に接続しているかどうかを自動的に検出し、現在のアクティブなサーバーを迅速に探索し、そのサーバーへの接続を提供します。 このリリースよりも前は、アプリケーションで接続文字列を設定し、`“MultisubnetFailover=true”` を含め、AlwaysOn 可用性グループに接続されていることを示す必要がありました。 `true` への接続キーワードを設定しないと、アプリケーションで AlwaysOn 可用性グループに接続中にタイムアウトが発生する可能性がありました。 このリリースを使うと、アプリケーションで [MultiSubnetFailover](assetId:///P:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover?qualifyHint=False&autoUpgrade=True) を `true` に設定する必要が "*なくなり*" ます。 Always On 可用性グループの SqlClient サポートの詳細については、「[高可用性障害復旧のための SqlClient サポート](../Topic/SqlClient%20Support%20for%20High%20Availability,%20Disaster%20Recovery.md)」をご覧ください。  
  
<a name="WPF461"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 Windows Presentation Foundation には、さまざまな改善と変更が含まれています。  
  
 パフォーマンスの向上  
 .NET Framework 4.6.1 で、タッチ イベントの開始の遅延が修正されました。 また、[RichTextBox](assetId:///T:System.Windows.Controls.RichTextBox?qualifyHint=False&autoUpgrade=True) コントロールの入力が高速入力時のレンダーのスレッドを停止させなくなりました。  
  
 スペル チェック機能の改善  
 WPF のスペル チェック機能が、追加の言語のスペル チェックのためにオペレーティング システムのサポートを利用するように、Windows 8.1 以降のバージョンで更新されました。  Windows 8.1 よりも前の Windows バージョンの機能の変更はありません。  
  
 以前のバージョンの .NET Framework と同様に、[TextBox](assetId:///T:System.Windows.Controls.TextBox?qualifyHint=False&autoUpgrade=True) コントロールまたは [RichTextBox](assetId:///T:System.Windows.Controls.RichTextBox?qualifyHint=False&autoUpgrade=True) ブロック用の言語が、次の順序で情報を探すことによって検出されます。  
  
-   `xml:lang` (存在する場合)。  
  
-   現在の入力言語。  
  
-   現在のスレッド カルチャ。  
  
 WPF での言語サポートの詳細については、[.NET Framework 4.6.1 機能に関する WPF ブログの記事](http://go.microsoft.com/fwlink/?LinkID=691819)を参照してください。  
  
 ユーザーごとのユーザー辞書の追加サポート  
 .NET Framework 4.6.1 では、WPF で、グローバルに登録されているユーザー辞書が認識されます。 この機能は、ユーザー辞書をコントロールごとに登録する機能に加えて使用できます。  
  
 以前のバージョンの WPF では、ユーザー辞書で除外された単語とオートコレクト リストが認識されませんでした。 `%AppData%\Microsoft\Spelling\<language tag>` ディレクトリに配置できるファイルの使用によって、これらが Windows 8.1 と Windows 10 でサポートされます。  これらのファイルには、次の規則が適用されます。  
  
-   これらのファイルには、拡張子の .dic (追加された単語の場合)、.exc (除外された単語の場合)、または .acl (オートコレクトの場合) が付いている必要があります。  
  
-   これらのファイルは、バイト オーダー マーク (BOM) で始まる UTF-16 LE プレーン テキストである必要があります。  
  
-   それぞれの行は、1 つの単語 (追加および除外された単語の一覧内)、または単語が縦棒 (“&#124;”) で区切られたオートコレクトのペア (オートコレクトの単語の一覧内) で構成される必要があります。  
  
-   これらのファイルは読み取り専用と見なされ、システムによって変更されることはありません。  
  
> [!NOTE]
>  これらの新しいファイル形式は、WPF スペル チェック API で直接サポートされるわけではありません。また、アプリケーションで WPF に提供されるユーザー辞書では以前と同様に .lex ファイルを使用する必要があります。  
  
 サンプル  
 MSDN に多数の [WPF サンプル](https://msdn.microsoft.com/library/ms771633.aspx)があります。 サンプルの利用状況に基づき、よく使用される 200 を超えるサンプルが、[オープン ソースの GitHub リポジトリ](https://github.com/Microsoft/WPF-Samples)に移動される予定です。 プル要求を送信するか、または[GitHub issue (GitHub の問題)](https://github.com/Microsoft/WPF-Samples/issues) を開いて、これらのサンプルの改善にご協力ください。  
  
 DirectX の拡張機能  
 WPF には、DX10 および Dx11 のコンテンツとの相互運用を容易にする、[D3DImage](assetId:///T:System.Windows.Interop.D3DImage?qualifyHint=False&autoUpgrade=True) の新しい実装を提供する [NuGet パッケージ](http://go.microsoft.com/fwlink/?LinkID=691342)が含まれています。 このパッケージのコードはオープン ソース化されており、[GitHub で](https://github.com/Microsoft/WPFDXInterop)入手できます。  
  
<a name="WWF461"></a>   
### <a name="windows-workflow-foundation-transactions"></a>Windows Workflow Foundation: トランザクション  
 [Transaction.EnlistPromotableSinglePhase](assetId:///Overload:System.Transactions.Transaction.EnlistPromotableSinglePhase?qualifyHint=True&autoUpgrade=True) メソッドで、MSDTC 以外の分散トランザクション マネージャーを使って、トランザクションをプロモート (昇格) できるようになりました。 このプロモートは、新しい [Transaction.EnlistPromotableSinglePhase(IPromotableSinglePhaseNotification, Guid)](assetId:///M:System.Transactions.Transaction.EnlistPromotableSinglePhase(System.Transactions.IPromotableSinglePhaseNotification,System.Guid)?qualifyHint=True&autoUpgrade=False) オーバーロードに GUID のトランザクション プロモーター識別子を指定することによって行います。 この操作が成功すると、そのトランザクションの機能に制限が加えられます。 MSDTC 以外のトランザクション プロモーターが登録される (参加する) と、次の各メソッドで MSDTC への昇格が必要になるため、これらのメソッドで [TransactionPromotionException](assetId:///T:System.Transactions.TransactionPromotionException?qualifyHint=False&autoUpgrade=True) がスローされます。  
  
-   [Transaction.EnlistDurable](assetId:///Overload:System.Transactions.Transaction.EnlistDurable?qualifyHint=True&autoUpgrade=True)  
  
-   [TransactionInterop.GetDtcTransaction](assetId:///M:System.Transactions.TransactionInterop.GetDtcTransaction(System.Transactions.Transaction)?qualifyHint=True&autoUpgrade=True)  
  
-   [TransactionInterop.GetExportCookie](assetId:///M:System.Transactions.TransactionInterop.GetExportCookie(System.Transactions.Transaction,System.Byte[])?qualifyHint=True&autoUpgrade=True)  
  
-   [TransactionInterop.GetTransmitterPropagationToken](assetId:///M:System.Transactions.TransactionInterop.GetTransmitterPropagationToken(System.Transactions.Transaction)?qualifyHint=True&autoUpgrade=True)  
  
 MSDTC 以外のトランザクション プロモーターが登録されると、そのプロモーターで定義するプロトコルを使用することで、そのプロモーターをその後の永続参加リストに使用する必要があります。 トランザクション プロモーターの [Guid](assetId:///T:System.Guid?qualifyHint=False&autoUpgrade=True) は、[PromoterType](assetId:///P:System.Transactions.Transaction.PromoterType?qualifyHint=False&autoUpgrade=True) プロパティを使って取得できます。 トランザクションがプロモートするとき、トランザクション プロモーターによって、プロモート済みトークンを表す [Byte](assetId:///T:System.Byte?qualifyHint=False&autoUpgrade=True) 配列が提供されます。 アプリケーションで、MSDTC 以外のプロモート済みトランザクションのプロモート済みトークンを [GetPromotedToken](assetId:///M:System.Transactions.Transaction.GetPromotedToken?qualifyHint=False&autoUpgrade=True) メソッドを使って取得できます。  
  
 新しい [Transaction.EnlistPromotableSinglePhase(IPromotableSinglePhaseNotification, Guid)](assetId:///M:System.Transactions.Transaction.EnlistPromotableSinglePhase(System.Transactions.IPromotableSinglePhaseNotification,System.Guid)?qualifyHint=True&autoUpgrade=False) オーバー ロードのユーザーは、昇格操作を正常に完了させるために、特定の呼び出し順序に従う必要があります。 これらの規則は、メソッドのドキュメントに記載されています。  
  
<a name="Profile461"></a>   
### <a name="profiling"></a>プロファイル  
 アンマネージ プロファイル API が、次のように拡張されました。  
  
 [ICorProfilerInfo7](../Topic/ICorProfilerInfo7%20Interface.md) インターフェイス内の PDB へのアクセスのサポートが向上  
 ASP.NET 5 では、アセンブリがメモリ内で Roslyn によってコンパイルされることがよりいっそう一般的になっています。 プロファイル ツールを作成する開発者にとって、これは従来ディスクにシリアル化されていた PDB が存在しなくなる可能性があることを意味しています。 プロファイル ツールでは、多くの場合 PDB を使用して、コード カバレッジや 1 行単位のパフォーマンス分析などのタスクのソース行に、コードをマップし戻します。 [ICorProfilerInfo7](../Topic/ICorProfilerInfo7%20Interface.md) インターフェイスは、メモリ内の PDB データにアクセスして、これらのプロファイル ツールを提供する 2 つの新しいメソッド、[ICorProfilerInfo7::GetInMemorySymbolsLength](../Topic/ICorProfilerInfo7::GetInMemorySymbolsLength%20Method.md) と [ICorProfilerInfo7::ReadInMemorySymbols](../Topic/ICorProfilerInfo7::ReadInMemorySymbols.md) を含むようになりました。これらの新しい API を使用すれば、プロファイラーでメモリ内の PDB の内容をバイト配列として取得してから、それを処理したり、ディスクにシリアル化したりできます。  
  
 ICorProfiler インターフェイスを使用したインストルメンテーションの改良  
 動的インストルメンテーションに `ICorProfiler` API の ReJit 機能を使用しているプロファイラーで、いくつかのメタデータを変更できるようになりました。 従来、このようなツールでは、いつでも IL をインストルメント化できましたが、メタデータを変更できるのはモジュールを読み込む時だけでした。 IL はメタデータを参照するため、実行できるインストルメンテーションの種類が限られています。 モジュールの読み込み後のメタデータの編集のサブセットをサポートするために、[ICorProfilerInfo7::ApplyMetaData](../Topic/ICorProfilerInfo7::ApplyMetaData%20Method.md) メソッドを追加することで (特に新しい `AssemblyRef`、`TypeRef`、`TypeSpec`、`MemberRef`、`MemberSpec`、および `UserString` の各レコードを追加することで)、これらの制限の一部を解消しました。 この変更により、はるかに広範な実行時インストルメンテーションが可能になります。  
  
<a name="NGEN461"></a>   
### <a name="native-image-generator-ngen-pdbs"></a>ネイティブ イメージ ジェネレーター (NGEN) PDB  
 マシン間のイベント トレースを使用すれば、ユーザーはマシン A 上でプログラムのプロファイリングを行い、マシン B 上でソース行のマッピングを使用して、プロファイリング データを確認できます。以前のバージョンの.NET Framework を使用する場合、ソースからネイティブへのマッピングを作成するには、ユーザーは、プロファイルされたコンピューターにあるすべてのモジュールとネイティブ イメージを、IL PDB が含まれた分析用コンピューターにコピーする必要がありました。 この処理は、Phone アプリケーションなどファイル サイズが比較的小さい場合には高速に実行されますが、これらのファイルのサイズがデスクトップ システム上で非常に大きくなる可能性があり、その場合コピーにかなりの時間を要する可能性があります。  
  
 NGen PDB を使用すれば、IL PDB に依存することなく、NGen で IL からネイティブへのマッピングが含まれた PDB を作成できます。 このマシン間のイベント トレース シナリオで必要なことは、コンピューター A で生成されたネイティブ イメージの PDB をコンピューター B にコピーすることと、[Debug Interface Access API](https://docs.microsoft.com/en-us/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) を使用して IL PDB のソースから IL へのマッピングとネイティブ イメージの PDB の IL からネイティブへのマッピングを読み取ることだけです。 両方のマッピングを組み合わせることで、ソースからネイティブへのマッピングが実現します。 ネイティブ イメージの PDB は、どのモジュールとネイティブ イメージよりもはるかにサイズが小さいため、コンピューター A からコンピューター B へのコピーの処理は非常に高速になります。  
  
<a name="v46"></a>   
## <a name="whats-new-in-net-2015"></a>.NET 2015 の新機能  
 .NET 2015 では、.NET Framework 4.6 と .NET Core が導入されています。 一部の新機能はその両方に適用され、その他の機能は .NET Framework 4.6 または .NET Core に固有です。  
  
-   **ASP.NET 5**  
  
     .NET 2015 には、ASP.NET 5 が含まれています。これは、最新のクラウド ベースのアプリを構築するのに非常に効率の良い .NET プラットフォームです。 このプラットフォームはモジュール形式であるため、アプリケーションで必要な機能のみを含めることができます。 IIS でホストすることも、カスタムのプロセスでセルフホストすることもできます。さらに同じサーバー上のさまざまなバージョンの .NET Framework でアプリを実行することも可能です。 クラウド展開用に設計されている新たな環境構成システムが含まれています。  
  
     MVC、Web API、および Web ページは、MVC 6 と呼ばれる 1 つのフレームワークに統合されています。 Visual Studio 2015 の新しいツールで ASP.NET 5 アプリをビルドします。 既存のアプリケーションは、この新しい .NET Framework で動作しますが、MVC 6 または SignalR 3 を使用するアプリケーションをビルドするには Visual Studio 2015 のプロジェクト システムを使用する必要があります。  
  
     詳細については、[ASP.NET 5](http://go.microsoft.com/fwlink/?LinkId=518238) に関するページを参照してください。  
  
-   **ASP.NET の更新プログラム**  
  
    -   **非同期応答フラッシュ用のタスク ベース API**  
  
         ASP.NET で、非同期応答フラッシュ用の単純なタスク ベース API である [HttpResponse.FlushAsync](assetId:///M:System.Web.HttpResponse.FlushAsync?qualifyHint=True&autoUpgrade=True) が提供されるようになりました。これにより、言語の `async/await` サポートを使って非同期的に応答をフラッシュできます。  
  
    -   `Model binding supports task-returning methods`  
  
         .NET Framework 4.5 では、Web フォーム ページやユーザー コントロールでの CRUD ベースのデータ操作に対して拡張可能なコード中心のアプローチを可能にするモデル バインド機能が ASP.NET に追加されました。 このモデル バインド システムで、[Task](assetId:///T:System.Threading.Tasks.Task?qualifyHint=False&autoUpgrade=True) を返すモデル バインド メソッドがサポートされるようになりました。 この機能により、Web フォーム開発者は Entity Framework などの ORM の新しいバージョンを使用するときに、データ バインド システムのように簡単に非同期のスケーラビリティ上のメリットを得ることができます。  
  
         非同期モデル バインドは、`aspnet:EnableAsyncModelBinding` 構成設定によって制御されます。  
  
        ```  
  
        <appSettings>  
           <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />  
        </appSettings>  
  
        ```  
  
         .NET Framework 4.6 を対象とするアプリでは、既定で `true` になります。 .NET Framework 4.6 で実行され、.NET Framework の以前のバージョンを対象とするアプリでは、既定で `false` になります。 有効にするには、この構成設定を `true` に設定します。  
  
    -   **HTTP/2 のサポート (Windows 10)**  
  
         [HTTP/2](http://www.wikipedia.org/wiki/HTTP/2) は HTTP プロトコルの新しいバージョンで、接続の使用状況が (クライアントとサーバー間のラウンド トリップ数の減少により) 大幅に改善されて、ユーザーが Web ページを読み込むときの遅延が軽減されています。  このプロトコルは単一のエクスペリエンスの一部として要求さる複数の成果物のために最適化されているので、HTTP/2 が最も役立つのは (サービスではなく) web ページです。 .NET Framework 4.6 では、HTTP/2 のサポートが ASP.NET に追加されました。 ネットワーク機能は複数のレイヤーで存在するので、HTTP/2 を有効にするために、Windows、IIS、および ASP.NET で新機能が必要とされていました。 ASP.NET で HTTP/2 を使用するには、Windows 10 を実行している必要があります。  
  
         HTTP/2 は、[System.Net.Http.HttpClient](assetId:///T:System.Net.Http.HttpClient?qualifyHint=True&autoUpgrade=True) API を使用する Windows 10 ユニバーサル Windows プラットフォーム (UWP) アプリでもサポートされ、既定で有効になります。  
  
         ASP.NET アプリケーションで [PUSH_PROMISE](http://http2.github.io/http2-spec/#PUSH_PROMISE) 機能を使う手段を提供するため、[PushPromise(String)](assetId:///M:System.Web.HttpResponse.PushPromise(System.String)?qualifyHint=False&autoUpgrade=False) と [PushPromise(String, String, NameValueCollection)](assetId:///M:System.Web.HttpResponse.PushPromise(System.String,System.String,System.Collections.Specialized.NameValueCollection)?qualifyHint=False&autoUpgrade=False) の 2 つのオーバーロードを持つ新しいメソッドが [HttpResponse](assetId:///T:System.Web.HttpResponse?qualifyHint=False&autoUpgrade=True) クラスに追加されました。  
  
        > [!NOTE]
        >  ASP.NET 5 では HTTP/2 がサポートされましたが、PUSH PROMISE 機能のサポートはまだ追加されていません。  
  
         ブラウザーと web サーバー (Windows 上の IIS) がすべての処理を実行します。 ユーザーの側で複雑な操作を実行する必要はありません。  
  
         [主要なブラウザーのほとんどは HTTP/2 をサポートしている](http://www.wikipedia.org/wiki/HTTP/2)ため、多くの場合、サーバーが HTTP/2 をサポートしていれば、ユーザーもそのメリットを得ることができます。  
  
    -   **トークン バインディング プロトコルのサポート**  
  
         Microsoft と Google は、[トークン バインディング プロトコル](https://github.com/TokenBinding/Internet-Drafts)と呼ばれる、認証のための新しいアプローチに共同で取り組んできました。 この前提となっているのは、犯罪者が (ブラウザー キャッシュ内の) 認証トークンを盗用することで、本来ならパスワードや他の特別な情報でセキュリティ保護されているリソース (銀行口座など) にアクセスできる可能性がある、ということです。 新しいプロトコルは、この問題を軽減することを目指しています。  
  
         トークン バインディング プロトコルは、Windows 10 でブラウザーの機能として実装されます。 ASP.NET アプリは、認証トークンの正当性が検証されるように、このプロトコルに参加します。 クライアントとサーバーの実装は、プロトコルによって指定されるエンド ツー エンドの保護を確立します。  
  
    -   **ランダムな文字列のハッシュ アルゴリズム**  
  
         .NET Framework 4.5 で、[ランダム化された文字列のハッシュ アルゴリズム](https://msdn.microsoft.com/library/jj152924.aspx)が導入されました。 しかし、ASP.NET の一部の機能は安定したハッシュ コードに依存していたため、この機能は ASP.NET ではサポートされませんでした。 .NET Framework 4.6 では、ランダムな文字列のハッシュ アルゴリズムがサポートされるようになりました。 この機能を有効にするには、`aspnet:UseRandomizedStringHashAlgorithm` 構成設定を使用します。  
  
        ```  
  
        <appSettings>  
           <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />  
        </appSettings>  
  
        ```  
  
-   **ADO.NET**  
  
     ADO .NET では、SQL Server 2016 Community Technology Preview 2 (CTP2) で使用できる Always Encrypted 機能がサポートされました。 SQL Server は、Always Encrypted 機能を使用して、暗号化されたデータに対して操作を実行できます。特に、サーバー上ではなく、ユーザーが信頼している環境内にアプリケーションと共に暗号化キーを保存できるようになりました。 Always Encrypted でユーザー データが保護されるので、DBA はプレーン テキスト データにアクセスできません。 データの暗号化と復号化は、ドライバー レベルで透過的に行われるので、既存のアプリケーションに対する変更が最小限に抑えられます。 詳細については、「[Always Encrypted (データベース エンジン)](https://msdn.microsoft.com/library/mt163865\(v=sql.130\).aspx)」および「[Always Encrypted (クライアント開発)](https://msdn.microsoft.com/library/mt147923\(v=sql.130\).aspx)」を参照してください。  
  
-   **マネージ コードの JIT コンパイラ (64 ビット)**  
  
     .NET Framework 4.6 の特徴の 1 つとして、新しいバージョンの 64 ビット JIT コンパイラ (RyuJIT というコードネームで呼ばれていたもの) があります。 この新しい 64 ビット コンパイラは、これまでの 64 ビット JIT コンパイラよりもパフォーマンスが大幅に向上しています。 新しい 64 ビット コンパイラは、.NET Framework 4.6 上で実行される 64 ビット プロセスで有効になります。 64 ビットまたは AnyCPU としてコンパイルされ、64 ビット オペレーティング システム上で実行されるアプリは、64 ビットで動作します。 新しいコンパイラへの移行をできる限り透過的に行うように注意を払いましたが、動作の変更が発生する可能性があります。 新しい JIT コンパイラの使用中に発生した問題については、直接お聞かせいただければと思います。 新しい 64 ビット JIT コンパイラに関連する可能性のある問題が発生した場合は、[Microsoft Connect](http://connect.microsoft.com/) にご連絡ください。  
  
     新しい 64 ビット JIT コンパイラには、ハードウェア SIMD アクセラレータ機能も含まれています。これを [System.Numerics](assetId:///N:System.Numerics?qualifyHint=False&autoUpgrade=True) 名前空間の SIMD 対応の型と組み合わせると、パフォーマンスが大幅に向上する可能性があります。  
  
-   **アセンブリ ローダーの改善**  
  
     アセンブリ ローダーで、対応する NGEN イメージの読み込み後に IL アセンブリをアンロードすることにより、メモリがより効率的に使用されるようになりました。 この変更は、仮想メモリが減少するため、特に大規模な 32 ビット アプリ (Visual Studio など) で有益であり、物理メモリの節約にもなります。  
  
-   **基本クラス ライブラリの変更点**  
  
     主なシナリオを利用できるようにするため、多くの新しい API が .NET Framework 4.6 に関連して追加されました。 変更点と追加点を以下に示します。  
  
    -   **IReadOnlyCollection\<T> implementations**  
  
         追加のコレクション [IReadOnlyCollection\<T>](assetId:///T:System.Collections.Generic.IReadOnlyCollection`1?qualifyHint=False&autoUpgrade=True) ([Queue<T\>](assetId:///T:System.Collections.Generic.Queue`1?qualifyHint=False&autoUpgrade=True)、[Stack\<T>](assetId:///T:System.Collections.Generic.Stack`1?qualifyHint=False&autoUpgrade=True) など) が実装されています。  
  
    -   **CultureInfo.CurrentCulture と CultureInfo.CurrentUICulture**  
  
         [CultureInfo.CurrentCulture](assetId:///P:System.Globalization.CultureInfo.CurrentCulture?qualifyHint=True&autoUpgrade=True) プロパティと [CultureInfo.CurrentUICulture](assetId:///P:System.Globalization.CultureInfo.CurrentUICulture?qualifyHint=True&autoUpgrade=True) プロパティが読み取り専用ではなく、読み取り/書き込み可能になりました。 新しい [CultureInfo](assetId:///T:System.Globalization.CultureInfo?qualifyHint=False&autoUpgrade=True) オブジェクトをこれらのプロパティに割り当てると、`Thread.CurrentThread.CurrentCulture` プロパティで現在定義されているスレッド カルチャと、`Thread.CurrentThread.CurrentUICulture` プロパティで現在定義されている UI スレッド カルチャも変更されます。  
  
    -   **ガベージ コレクション (GC) の機能強化**  
  
         [GC](assetId:///T:System.GC?qualifyHint=False&autoUpgrade=True) クラスに [TryStartNoGCRegion](assetId:///M:System.GC.TryStartNoGCRegion(System.Int64)?qualifyHint=False&autoUpgrade=True) メソッドと [EndNoGCRegion](assetId:///M:System.GC.EndNoGCRegion?qualifyHint=False&autoUpgrade=True) メソッドが含まれるようになりました。これらのメソッドを使うとクリティカル パスの実行中にガベージ コレクションを不許可にできます。  
  
         [GC.Collect(Int32, GCCollectionMode, Boolean, Boolean)](assetId:///M:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean,System.Boolean)?qualifyHint=True&autoUpgrade=False) メソッドの新しいオーバーロードを使って、小さなオブジェクト ヒープと大きなオブジェクト ヒープの両方に関して、スイープして圧縮するのか、スイープのみを行うのかを制御できます。  
  
    -   **SIMD が有効な型**  
  
         [System.Numerics](assetId:///N:System.Numerics?qualifyHint=False&autoUpgrade=True) 名前空間には、[Matrix3x2](assetId:///T:System.Numerics.Matrix3x2?qualifyHint=False&autoUpgrade=True)、[Matrix4x4](assetId:///T:System.Numerics.Matrix4x4?qualifyHint=False&autoUpgrade=True)、[Plane](assetId:///T:System.Numerics.Plane?qualifyHint=False&autoUpgrade=True)、[Quaternion](assetId:///T:System.Numerics.Quaternion?qualifyHint=False&autoUpgrade=True)、[Vector2](assetId:///T:System.Numerics.Vector2?qualifyHint=False&autoUpgrade=True)、[Vector3](assetId:///T:System.Numerics.Vector3?qualifyHint=False&autoUpgrade=True)、[Vector4](assetId:///T:System.Numerics.Vector4?qualifyHint=False&autoUpgrade=True) など、いくつかの SIMD 対応の型が含まれるようになりました。  
  
         新しい 64 ビット JIT コンパイラにはハードウェア SIMD アクセラレータ機能も含まれているため、新しい 64 ビット JIT コンパイラで SIMD 対応の型を使用すると、パフォーマンスが大幅に向上します。  
  
    -   **暗号の更新**  
  
         [System.Security.Cryptography](assetId:///N:System.Security.Cryptography?qualifyHint=True&autoUpgrade=True) API は、[Windows CNG 暗号 API](https://msdn.microsoft.com/library/windows/desktop/aa376214.aspx) をサポートするように更新されています。 以前のバージョンの .NET Framework は、[System.Security.Cryptography](assetId:///N:System.Security.Cryptography?qualifyHint=True&autoUpgrade=True) の実装の基礎として、[それより前のバージョンの Windows 暗号化 API](https://msdn.microsoft.com/library/windows/desktop/aa380255.aspx) に完全に依存していました。 CNG API は特定のカテゴリのアプリにとって重要な[最新の暗号アルゴリズム](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx#suite_b_support)をサポートするものであるため、CNG API をサポートしてほしいというリクエストが寄せられていました。  
  
         .NET Framework 4.6 には、Windows CNG 暗号化 API をサポートするために、次の新しい機能強化が含まれています。  
  
        -   可能な場合に CAPI ベースの実装ではなく CNG ベースの実装を返す X509 証明書用の一連の拡張メソッド `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` および `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`  (一部のスマート カードなどでは現在も CAPI が必要であり、API がフォールバックを処理します)。  
  
        -   RSA アルゴリズムの CNG の実装を提供する、[System.Security.Cryptography.RSACng](assetId:///T:System.Security.Cryptography.RSACng?qualifyHint=True&autoUpgrade=True) クラス。  
  
        -   一般的な操作でキャストを不要にする RSA API の機能強化。 たとえば、以前のバージョンの .NET Framework で [X509Certificate2](assetId:///T:System.Security.Cryptography.X509Certificates.X509Certificate2?qualifyHint=False&autoUpgrade=True) オブジェクトを使用してデータを暗号化するには、次のようなコードが必要です。  
  
<!-- TODO: review snippet reference              [!CODE [WhatsNew.Casting#1](../CodeSnippet/VS_Snippets_CLR/whatsnew.casting#1)]  -->  
  
             Code that uses the new cryptography APIs in the .NET Framework 4.6 can be rewritten as follows to avoid the cast.  
  
<!-- TODO: review snippet reference              [!CODE [WhatsNew.Casting#2](../CodeSnippet/VS_Snippets_CLR/whatsnew.casting#2)]  -->  
  
    -   **日付および時間と UNIX 時間の変換のサポート**  
  
         日付値および時間値と UNIX 時間の変換をサポートするため、次の新しいメソッドが [DateTimeOffset](assetId:///T:System.DateTimeOffset?qualifyHint=False&autoUpgrade=True) 構造体に追加されました。  
  
        -   [DateTimeOffset.FromUnixTimeSeconds](assetId:///M:System.DateTimeOffset.FromUnixTimeSeconds(System.Int64)?qualifyHint=True&autoUpgrade=True)  
  
        -   [DateTimeOffset.FromUnixTimeMilliseconds](assetId:///M:System.DateTimeOffset.FromUnixTimeMilliseconds(System.Int64)?qualifyHint=True&autoUpgrade=True)  
  
        -   [DateTimeOffset.ToUnixTimeSeconds](assetId:///M:System.DateTimeOffset.ToUnixTimeSeconds?qualifyHint=True&autoUpgrade=True)  
  
        -   [DateTimeOffset.ToUnixTimeMilliseconds](assetId:///M:System.DateTimeOffset.ToUnixTimeMilliseconds?qualifyHint=True&autoUpgrade=True)  
  
    -   **互換性スイッチ**  
  
         新しい [AppContext](assetId:///T:System.AppContext?qualifyHint=False&autoUpgrade=True) クラスは、ライブラリの作成者が統一された新機能のオプトアウト メカニズムをユーザーに提供できるようにする、新しい互換性機能を追加します。 これは、オプトアウト要求を伝達するために、コンポーネント間に疎結合のコントラクトを確立します。 通常、この機能は既存の機能が変更されるときに重要となります。 それに対して、新しい機能には暗黙のオプトインが既に存在しています。  
  
         [AppContext](assetId:///T:System.AppContext?qualifyHint=False&autoUpgrade=True) によって、ライブラリは互換性スイッチを定義し公開します。また、それらに依存するコードは、それらのスイッチを設定してライブラリの動作に影響を与えることができます。 ライブラリは、既定では新しい機能を提供し、スイッチが設定されている場合のみそれを変更する (つまり以前の機能を提供する) ことができます。  
  
         アプリケーション (またはライブラリ) は、依存するライブラリが定義したスイッチの値 (常に [Boolean](assetId:///T:System.Boolean?qualifyHint=False&autoUpgrade=True) 値) を宣言できます。 スイッチは常に暗黙的に `false` です。 スイッチを `true` に設定すると、それが有効になります。 スイッチを明示的に `false` に設定すると、新しい動作が提供されます。  
  
        ```csharp  
        AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);  
        ```  
  
         ライブラリは、コンシューマーがスイッチの値を宣言したことを確認してから、それを適切に実行する必要があります。  
  
        ```  
  
        if (!AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", out shouldThrow))   
        {  
           // This is the case where the switch value was not set by the application.   
           // The library can choose to get the value of shouldThrow by other means.   
           // If no overrides nor default values are specified, the value should be 'false'.   
           // A false value implies the latest behavior.  
        }  
  
           // The library can use the value of shouldThrow to throw exceptions or not.  
           if (shouldThrow)   
           {  
              // old code  
           }  
           else {  
              // new code  
           }  
        }  
  
        ```  
  
         スイッチは、ライブラリによって公開される正式なコントラクトであるため、一貫性のある形式を使用することをお勧めします。 2 つの明確な形式を次に示します。  
  
        -   *Switch*.*namespace*.*switchname*  
  
        -   *Switch*.*library*.*switchname*  
  
    -   **タスク ベースの非同期パターン (TAP) の変更点**  
  
         .NET Framework 4.6 をターゲットとするアプリの場合、[Task](assetId:///T:System.Threading.Tasks.Task?qualifyHint=False&autoUpgrade=True) オブジェクトと [Task\<TResult>](assetId:///T:System.Threading.Tasks.Task`1?qualifyHint=False&autoUpgrade=True) オブジェクトは、呼び出し元のスレッドのカルチャと UI カルチャを継承します。 以前のバージョンの .NET Framework をターゲットするとアプリまたは特定のバージョンの .NET Framework をターゲットとしないアプリの動作には影響を及ぼしません。 詳細については、[CultureInfo](assetId:///T:System.Globalization.CultureInfo?qualifyHint=False&autoUpgrade=True) クラスのトピックの「カルチャとタスク ベースの非同期の操作」セクションをご覧ください。  
  
         [System.Threading.AsyncLocal\<T>](assetId:///T:System.Threading.AsyncLocal`1?qualifyHint=True&autoUpgrade=True) クラスを使うと、`async` メソッドなど、特定の非同期制御フローに対してローカルなアンビエント データを表すことができます。 これは、スレッド間でデータを保持するために使用できます。 [AsyncLocal<T\>.Value](assetId:///P:System.Threading.AsyncLocal`1.Value?qualifyHint=True&autoUpgrade=True) プロパティの明示的な変更やスレッドでのコンテキスト変換の発生などによってアンビエント データが変更されるたびに通知されるコールバック メソッドを定義することもできます。  
  
         タスク ベースの非同期パターン (TAP) に、特定の状態で完了したタスクを返す 3 つの便利なメソッド [Task.CompletedTask](assetId:///P:System.Threading.Tasks.Task.CompletedTask?qualifyHint=True&autoUpgrade=True)、[Task.FromCanceled](assetId:///M:System.Threading.Tasks.Task.FromCanceled(System.Threading.CancellationToken)?qualifyHint=True&autoUpgrade=True)、[Task.FromException](assetId:///M:System.Threading.Tasks.Task.FromException(System.Exception)?qualifyHint=True&autoUpgrade=True) が追加されました。  
  
         [NamedPipeClientStream](assetId:///T:System.IO.Pipes.NamedPipeClientStream?qualifyHint=False&autoUpgrade=True) クラスで、新しい [ConnectAsync](assetId:///M:System.IO.Pipes.NamedPipeClientStream.ConnectAsync?qualifyHint=False&autoUpgrade=True) メソッドによる非同期通信がサポートされるようになりました。 メソッドをオーバーライドします。  
  
    -   **EventSource がイベント ログへの書き込みをサポート**  
  
         コンピューター上で作成された既存の ETW セッションに加えて、[EventSource](assetId:///T:System.Diagnostics.Tracing.EventSource?qualifyHint=False&autoUpgrade=True) クラスを使って管理または操作メッセージをイベント ログに記録できるようになりました。 以前は、この機能のために Microsoft.Diagnostics.Tracing.EventSource NuGet パッケージを使用する必要がありました。 この機能は .NET Framework 4.6 に組み込まれました。  
  
         NuGet パッケージと .NET Framework 4.6 は、どちらも次の機能によって更新されています。  
  
        -   **ダイナミック イベント**  
  
             イベント メソッドを作成せずに、実行時にイベントを定義できます。  
  
        -   **リッチ ペイロード**  
  
             特別な属性が指定されたクラスや配列に加えて、プリミティブ型もペイロードとして渡すことができます。  
  
        -   **アクティビティの追跡**  
  
             Start イベントと Stop イベントの間のイベントに、現在アクティブなすべてのアクティビティを表す ID が付けられます。  
  
         これらの機能をサポートするため、[EventSource](assetId:///T:System.Diagnostics.Tracing.EventSource?qualifyHint=False&autoUpgrade=True) クラスにオーバーロードされた [Write](assetId:///M:System.Diagnostics.Tracing.EventSource.Write(System.String)?qualifyHint=False&autoUpgrade=True) メソッドが追加されました。  
  
-   **Windows Presentation Foundation (WPF)**  
  
    -   **HDPI の強化**  
  
         .NET Framework 4.6 では、WPF での HDPI サポートが強化されました。 境界があるコントロールでのクリッピングの発生を減らすため、レイアウトの丸め処理が変更されました。 既定では、この機能は [TargetFrameworkAttribute](assetId:///T:System.Runtime.Versioning.TargetFrameworkAttribute?qualifyHint=False&autoUpgrade=True) が .NET 4.6 に設定されている場合にのみ有効です。  以前のバージョンの Framework を対象とするアプリケーションが .NET Framework 4.6 で実行される場合は、app.config ファイルの [\<runtime>](../Topic/%3Cruntime%3E%20Element.md) セクションに次の行を追加することで、新しい動作を選択できます。  
  
        ```  
  
        <AppContextSwitchOverrides  
        value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"  
        />  
  
        ```  
  
         異なる DPI 設定を持つ (マルチ DPI セットアップの) 複数のモニターにまたがる WPF ウィンドウは、ブラック アウト領域なしで完全にレンダリングされるようになりました。 この動作の選択を解除するには、app.config ファイルの `<appSettings>` セクションに次の行を追加して、この新しい動作を無効にします。  
  
        ```  
  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
  
        ```  
  
         DPI 設定に基づいて自動的に正しいカーソルを読み込む機能のサポートが [System.Windows.Input.Cursor](assetId:///T:System.Windows.Input.Cursor?qualifyHint=True&autoUpgrade=True) に追加されました。  
  
    -   **タッチの改善**  
  
         タッチで予期しない動作が発生するという、お客様から報告された [Connect](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) の問題が .NET Framework 4.6 で対処されました。 Windows 8.1 以降では、Windows ストア アプリケーションと WPF アプリケーションのダブルタップのしきい値が同じになりました。  
  
    -   **透過的な子ウィンドウのサポート**  
  
         .NET Framework 4.6 の WPF では、Windows 8.1 以降の透過的な子ウィンドウがサポートされます。 これにより、最上位レベルのウィンドウ内に四角形でない透過的な子ウィンドウを作成できます。 この機能を有効にするには、[HwndSourceParameters.UsesPerPixelTransparency](assetId:///P:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency?qualifyHint=True&autoUpgrade=True) プロパティを `true` に設定します。  
  
-   **Windows Communication Foundation (WCF)**  
  
    -   **SSL のサポート**  
  
         WCF で、NetTcp をトランスポート セキュリティおよびクライアント認証と共に使用する場合に、SSL のバージョンとして SSL 3.0 および TLS 1.0 に加えて TLS 1.1 および TLS 1.2 がサポートされるようになりました。 使用するプロトコルを選択することも、安全性の低い古いプロトコルを無効化することもできるようになりました。 これを行うには、[SslProtocols](assetId:///P:System.ServiceModel.TcpTransportSecurity.SslProtocols?qualifyHint=False&autoUpgrade=True) プロパティを設定するか、または構成ファイルに以下を追加します。  
  
        ```  
        <netTcpBinding>  
           <binding>  
              <security mode= "None|Transport|Message|TransportWithMessageCredential" >  
                 <transport clientCredentialType="None|Windows|Certificate"  
                            protectionLevel="None|Sign|EncryptAndSign"  
                            sslProtocols="Ssl3|Tls1|Tls11|Tls12">  
                    </transport>  
              </security>  
           </binding>  
        </netTcpBinding>  
  
        ```  
  
    -   **異なる HTTP 接続によるメッセージの送信**  
  
         WCF で、ユーザーが別の基になる HTTP 接続を使用して特定のメッセージを送信できるようになりました。 これには、2 つの方法があります。  
  
        -   **接続グループ名プレフィックスの使用**  
  
             ユーザーは、WCF で接続グループ名のプレフィックスとして使用される文字列を指定できます。 異なるプレフィックスを持つ 2 つのメッセージは、別の基になる HTTP 接続を使用して送信されます。 プレフィックスを設定するには、メッセージの [Message.Properties](assetId:///P:System.ServiceModel.Channels.Message.Properties?qualifyHint=True&autoUpgrade=True) プロパティにキー/値のペアを追加します。 キーは "HttpTransportConnectionGroupNamePrefix" で、値は使用するプレフィックスです。  
  
        -   **異なるチャネル ファクトリの使用**  
  
             ユーザーは、異なるチャネル ファクトリによって作成されたチャネルを使用して送信されるメッセージで別の基になる HTTP 接続を使用する機能を有効にすることもできます。 この機能を有効にするには、ユーザーが次の `appSetting` を `true` に設定する必要があります。  
  
            ```  
  
            <appSettings>  
               <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />  
            </appSettings>  
  
            ```  
  
-   **Windows Workflow Foundation (WWF)**  
  
     順序不定の操作要求がタイムアウトする前に未処理の「非プロトコル」ブックマークが存在する場合に、ワークフロー サービスが要求を保持する秒数を指定できるようになりました。 「非プロトコル」ブックマークとは、未処理の Receive アクティビティに関連付けられていないブックマークです。 一部のアクティビティはその実装内で非プロトコル ブックマークを作成するため、必ずしも非プロトコル ブックマークの存在が明らかにわかるとは限りません。 例として State や Pick などがあります。 ステート マシンを使用して実装されたワークフロー サービスや、Pick アクティビティを含むワークフロー サービスがある場合は、非プロトコル ブックマークが存在する可能性が高くなります。 この間隔を指定するには、app.config ファイルの `appSettings` セクションに次のような行を追加します。  
  
    ```  
    <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>  
    ```  
  
     既定値は 60 秒です。 `value` を 0 に設定すると、順序不定の要求はただちに拒否され、次のようなテキストを含むエラーが返されます。  
  
    ```Output  
    Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.   
    ```  
  
     これは、順序不定の操作メッセージを受信し、非プロトコル ブックマークが存在しない場合に受信するメッセージと同じです。  
  
     `FilterResumeTimeoutInSeconds` 要素の値がゼロ以外で、非プロトコル ブックマークが存在し、タイムアウト間隔が終了した場合、その操作は失敗し、タイムアウト メッセージが発生します。  
  
-   **トランザクション**  
  
     [TransactionException](assetId:///T:System.Transactions.TransactionException?qualifyHint=False&autoUpgrade=True) から派生した例外がスローされる原因となったトランザクションに、分散トランザクション識別子を含めることができるようになりました。 これを行うには、次のキーを app.config ファイルの `appSettings` セクションに追加します。  
  
    ```  
    <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>   
    ```  
  
     既定値は `false` です。  
  
-   **ネットワーク**  
  
    -   **ソケットの再利用**  
  
         Windows 10 には、送信 TCP 接続のローカル ポートを再利用してコンピューターのリソースを効率的に使用する新しいスケーラビリティの高いネットワーク アルゴリズムが含まれています。 .NET Framework 4.6 では、この新しいアルゴリズムがサポートされ、.NET アプリで新しい動作を利用できます。 以前のバージョンの Windows では、人工的な同時接続の制限 (通常は動的なポート範囲の既定のサイズである 16,384) があったため、負荷がかかったときにポートが使い尽くされ、サービスのスケーラビリティが制限されることがありました。  
  
         .NET Framework 4.6 では、ポートの再利用を有効にする次の 2 つの新しい API が追加され、同時接続に対する 64K の制限が実質的になくなりました。  
  
        -   [SocketOptionName.ReuseUnicastPort](assetId:///T:System.Net.Sockets.SocketOptionName?qualifyHint=True&autoUpgrade=True) 列挙値。  
  
        -   [ServicePointManager.ReusePort](assetId:///P:System.Net.ServicePointManager.ReusePort?qualifyHint=True&autoUpgrade=True) プロパティ。  
  
         既定では、`HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` レジストリ キーの `HWRPortReuseOnSocketBind` の値が 0x1 に設定されないかぎり、[ServicePointManager.ReusePort](assetId:///P:System.Net.ServicePointManager.ReusePort?qualifyHint=True&autoUpgrade=True) プロパティは `false` になります。 HTTP 接続でのローカル ポートの再利用を有効にするには、[ServicePointManager.ReusePort](assetId:///P:System.Net.ServicePointManager.ReusePort?qualifyHint=True&autoUpgrade=True) プロパティを `true` に設定します。 これにより、[HttpClient](assetId:///T:System.Net.Http.HttpClient?qualifyHint=False&autoUpgrade=True) および [HttpWebRequest](assetId:///T:System.Net.HttpWebRequest?qualifyHint=False&autoUpgrade=True) からの外向きのすべての TCP ソケット接続で Windows 10 の新しいソケット オプション [SO_REUSE_UNICASTPORT](https://msdn.microsoft.com/library/windows/desktop/ms740532.aspx) が使われるようになるため、ローカル ポートの再利用が可能になります。  
  
         ソケット専用のアプリケーションを作成する開発者は、[Socket.SetSocketOption](assetId:///M:System.Net.Sockets.Socket.SetSocketOption(System.Net.Sockets.SocketOptionLevel,System.Net.Sockets.SocketOptionName,System.Byte[])?qualifyHint=True&autoUpgrade=True) などのメソッドを呼び出すときに [SocketOptionName.ReuseUnicastPort](assetId:///T:System.Net.Sockets.SocketOptionName?qualifyHint=True&autoUpgrade=True) オプションを指定することにより、送信ソケットでバインド中にローカル ポートを再利用できるようになります。  
  
    -   **国際ドメイン名と PunyCode のサポート**  
  
         [Uri](assetId:///T:System.Uri?qualifyHint=False&autoUpgrade=True) クラスに新しいプロパティ [IdnHost](assetId:///P:System.Uri.IdnHost?qualifyHint=False&autoUpgrade=True) が追加され、国際ドメイン名と PunyCode のサポートが強化されました。  
  
-   **Windows フォーム コントロールでのサイズ変更**  
  
     この機能が .NET Framework 4.6 にも拡張されました。[DomainUpDown](assetId:///T:System.Windows.Forms.DomainUpDown?qualifyHint=False&autoUpgrade=True)、[NumericUpDown](assetId:///T:System.Windows.Forms.NumericUpDown?qualifyHint=False&autoUpgrade=True)、[DataGridViewComboBoxColumn](assetId:///T:System.Windows.Forms.DataGridViewComboBoxColumn?qualifyHint=False&autoUpgrade=True)、[DataGridViewColumn](assetId:///T:System.Windows.Forms.DataGridViewColumn?qualifyHint=False&autoUpgrade=True)、[ToolStripSplitButton](assetId:///T:System.Windows.Forms.ToolStripSplitButton?qualifyHint=False&autoUpgrade=True) 型、および [UITypeEditor](assetId:///T:System.Drawing.Design.UITypeEditor?qualifyHint=False&autoUpgrade=True) を描画するときに使用する [Bounds](assetId:///P:System.Drawing.Design.PaintValueEventArgs.Bounds?qualifyHint=False&autoUpgrade=True) プロパティで指定される四角形も含まれるようになりました。  
  
     これはオプトイン機能です。 この機能を有効にするには、アプリケーション構成 (app.config) ファイルで `EnableWindowsFormsHighDpiAutoResizing` 要素を `true` に設定します。  
  
    ```  
  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
  
    ```  
  
-   **コード ページのエンコーディングのサポート**  
  
     .NET Core は、本来 Unicode エンコードをサポートし、既定ではコード ページ エンコーディングに関するサポートは限定的です。 [Encoding.RegisterProvider](assetId:///M:System.Text.Encoding.RegisterProvider(System.Text.EncodingProvider)?qualifyHint=True&autoUpgrade=True) メソッドを使ってコード ページ エンコーディングを登録することで、.NET Framework では利用できるものの .NET Core ではサポートされていないコード ページ エンコーディングのサポートを追加できます。 詳細については、[System.Text.CodePagesEncodingProvider](xref:System.Text.CodePagesEncodingProvider) クラスのドキュメントをご覧ください。  
  
-   **.NET ネイティブ**  
  
     .NET Core をターゲットとし、C# または Visual Basic で作成されている Windows 10 用の Windows アプリは、IL ではなくネイティブ コードにアプリをコンパイルする新しい技術を活用できます。 これで、起動時間と実行時間がより速いアプリを生成できます。 詳しくは、「[.NET ネイティブによるアプリのコンパイル](../Topic/Compiling%20Apps%20with%20.NET%20Native.md)」をご覧ください。 JIT コンパイルと NGEN による結果の違い、およびコードにおけるその影響の概要については、「[.NET ネイティブとコンパイル](../Topic/.NET%20Native%20and%20Compilation.md)」をご覧ください。  
  
     アプリは、Visual Studio 2015 でコンパイルするときに、既定でネイティブ コードにコンパイルされます。 詳しくは、「[.NET ネイティブの概要](../Topic/Getting%20Started%20with%20.NET%20Native.md)」をご覧ください。  
  
     .NET ネイティブ アプリのデバッグをサポートするため、アンマネージ デバッグ APIに対して数多くの新しいインターフェイスと列挙型が追加されました。 詳しくは、「[デバッグ (アンマネージ API リファレンス)](../Topic/Debugging%20\(Unmanaged%20API%20Reference\).md)」をご覧ください。  
  
-   **オープン ソースの .NET Framework パッケージ**  
  
     変更できないコレクションなどの .NET Core のパッケージ、[SIMD API](http://go.microsoft.com/fwlink/?LinkID=518639)、および [System.Net.Http](assetId:///N:System.Net.Http?qualifyHint=False&autoUpgrade=True) 名前空間に含まれるようなネットワーク API は、[GitHub](https://github.com/) でオープン ソース パッケージとして入手できるようになりました。 このコードにアクセスするには、[GitHub で NetFx](http://go.microsoft.com/fwlink/?LinkID=518634) を参照してください。 これらのパッケージの詳細、および投稿方法については、「[.NET Core とオープン ソース](../Topic/.NET%20Core%20and%20Open-Source.md)」および [GitHub の .NET ホーム ページ](http://go.microsoft.com/fwlink/?LinkID=518635)を参照してください。  
  
 [ページのトップへ](#introduction)  
  
<a name="v452"></a>   
## <a name="whats-new-in-the-net-framework-452"></a>.NET Framework 4.5.2 の新機能  
  
-   **ASP.NET アプリ用の新しい API。** 新しい [HttpResponse.AddOnSendingHeaders](assetId:///M:System.Web.HttpResponse.AddOnSendingHeaders(System.Action{System.Web.HttpContext})?qualifyHint=True&autoUpgrade=True) メソッドおよび [HttpResponseBase.AddOnSendingHeaders](assetId:///M:System.Web.HttpResponseBase.AddOnSendingHeaders(System.Action{System.Web.HttpContextBase})?qualifyHint=True&autoUpgrade=True) メソッドを使うと、応答がクライアント アプリにフラッシュされるときに、応答ヘッダーとステータス コードを検査および変更することができます。 これらのメソッドを [PreSendRequestHeaders](assetId:///E:System.Web.HttpApplication.PreSendRequestHeaders?qualifyHint=False&autoUpgrade=True) イベントおよび [PreSendRequestContent](assetId:///E:System.Web.HttpApplication.PreSendRequestContent?qualifyHint=False&autoUpgrade=True) イベントの代わりに使うことを検討してください。より効率的で信頼性が高くなります。  
  
     [HostingEnvironment.QueueBackgroundWorkItem](assetId:///M:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem(System.Action{System.Threading.CancellationToken})?qualifyHint=True&autoUpgrade=True) メソッドにより、小さなバックグラウンド作業項目をスケジュールできます。 ASP.NET はこれらの項目を追跡し、すべてのバックグラウンド作業項目が完了するまで IIS が突然ワーカー プロセスを終了しないようにします。 このメソッドは、ASP.NET マネージ アプリ ドメインの外部で呼び出すことはできません。  
  
     新しい [HttpResponse.HeadersWritten](assetId:///P:System.Web.HttpResponse.HeadersWritten?qualifyHint=True&autoUpgrade=False) プロパティと [HttpResponseBase.HeadersWritten](assetId:///P:System.Web.HttpResponseBase.HeadersWritten?qualifyHint=True&autoUpgrade=False) プロパティは、応答ヘッダーが書き込まれたかどうかを示すブール値を返します。 これらのプロパティを使って、[HttpResponse.StatusCode](assetId:///P:System.Web.HttpResponse.StatusCode?qualifyHint=True&autoUpgrade=True) (ヘッダーが書き込まれた場合に例外をスローする) などの API への呼び出しが成功することを確認できます。  
  
-   **Windows フォーム コントロールでのサイズ変更** この機能が拡張されました。 これにより、システム DPI 設定を使用して、次の追加コントロールのコンポーネント (例: コンボ ボックスのドロップダウン矢印) をサイズ変更できます。  
  
     [ComboBox](assetId:///T:System.Windows.Forms.ComboBox?qualifyHint=False&autoUpgrade=True)   
     [ToolStripComboBox](assetId:///T:System.Windows.Forms.ToolStripComboBox?qualifyHint=False&autoUpgrade=True)   
     [ToolStripMenuItem](assetId:///T:System.Windows.Forms.ToolStripMenuItem?qualifyHint=False&autoUpgrade=True)   
     [Cursor](assetId:///T:System.Windows.Forms.Cursor?qualifyHint=False&autoUpgrade=True)   
     [DataGridView](assetId:///T:System.Windows.Forms.DataGridView?qualifyHint=False&autoUpgrade=True)   
     [DataGridViewComboBoxColumn](assetId:///T:System.Windows.Forms.DataGridViewComboBoxColumn?qualifyHint=False&autoUpgrade=True)  
  
     これはオプトイン機能です。 この機能を有効にするには、アプリケーション構成 (app.config) ファイルで `EnableWindowsFormsHighDpiAutoResizing` 要素を `true` に設定します。  
  
    ```  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
    ```  
  
-   **新しいワークフロー機能。** [EnlistPromotableSinglePhase](assetId:///M:System.Transactions.Transaction.EnlistPromotableSinglePhase(System.Transactions.IPromotableSinglePhaseNotification)?qualifyHint=False&autoUpgrade=True) メソッドを使っている (および、結果として [IPromotableSinglePhaseNotification](assetId:///T:System.Transactions.IPromotableSinglePhaseNotification?qualifyHint=False&autoUpgrade=True) インターフェイスを実装している) リソース マネージャーは、新しい [Transaction.PromoteAndEnlistDurable](assetId:///M:System.Transactions.Transaction.PromoteAndEnlistDurable(System.Guid,System.Transactions.IPromotableSinglePhaseNotification,System.Transactions.ISinglePhaseNotification,System.Transactions.EnlistmentOptions)?qualifyHint=True&autoUpgrade=True) メソッドを使って、次のことを要求できます。  
  
    -   トランザクションを Microsoft 分散トランザクション コーディネーター (MSDTC) トランザクションに昇格します。  
  
    -   [IPromotableSinglePhaseNotification](assetId:///T:System.Transactions.IPromotableSinglePhaseNotification?qualifyHint=False&autoUpgrade=True) を、単一フェーズ コミットをサポートする永続参加リストである [ISinglePhaseNotification](assetId:///T:System.Transactions.ISinglePhaseNotification?qualifyHint=False&autoUpgrade=True) で置換する。  
  
     これは同じアプリ ドメイン内で実行でき、MSDTC とやり取りして昇格を実行するためにアンマネージ コードを追加する必要はありません。 新しいメソッドを呼び出すことができるのは、[System.Transactions](assetId:///N:System.Transactions?qualifyHint=True&autoUpgrade=True) から、昇格可能な参加リストによって実装された [IPromotableSinglePhaseNotification](assetId:///T:System.Transactions.IPromotableSinglePhaseNotification?qualifyHint=False&autoUpgrade=True)`Promote` メソッドへの未処理の呼び出しがある場合のみです。  
  
-   **プロファイリングの機能強化。** 次の新しいアンマネージ プロファイリング API により、さらに信頼性の高いプロファイリングを提供します。  
  
     [COR_PRF_ASSEMBLY_REFERENCE_INFO 構造体](../Topic/COR_PRF_ASSEMBLY_REFERENCE_INFO%20Structure.md)   
     [COR_PRF_HIGH_MONITOR 列挙型](../Topic/COR_PRF_HIGH_MONITOR%20Enumeration.md)   
     [GetAssemblyReferences メソッド](../Topic/ICorProfilerCallback6::GetAssemblyReferences%20Method.md)   
     [GetEventMask2 メソッド](../Topic/ICorProfilerInfo5::GetEventMask2%20Method.md)   
     [SetEventMask2 メソッド](../Topic/ICorProfilerInfo5::SetEventMask2%20Method.md)   
     [AddAssemblyReference メソッド](../Topic/ICorProfilerAssemblyReferenceProvider::AddAssemblyReference%20Method.md)  
  
     以前の `ICorProfiler` の実装は、依存アセンブリの遅延読み込みをサポートしていました。 新しいプロファイリング API では、プロファイラーにより挿入される依存アセンブリを、アプリの完全な初期化後に読み込むのではなく、すぐに読み込む必要があります。 この変更は、既存の `ICorProfiler` API のユーザーには影響しません。  
  
-   **デバッグの機能強化。** 次の新しいアンマネージド デバッグ API により、プロファイラーとの統合性が向上しました。 これにより、ダンプのデバッグ時にコンパイラ ReJIT 要求により作成されたローカル変数やコードだけでなく、プロファイラーにより挿入されたメタデータにアクセスできます。  
  
     [SetWriteableMetadataUpdateMode メソッド](../Topic/ICorDebugProcess7::SetWriteableMetadataUpdateMode%20Method.md)   
     [EnumerateLocalVariablesEx メソッド](../Topic/ICorDebugILFrame4::EnumerateLocalVariablesEx%20Method.md)   
     [GetLocalVariableEx メソッド](../Topic/ICorDebugILFrame4::GetLocalVariableEx%20Method.md)   
     [GetCodeEx メソッド](../Topic/ICorDebugILFrame4::GetCodeEx%20Method.md)   
     [GetActiveReJitRequestILCode メソッド](../Topic/ICorDebugFunction3::GetActiveReJitRequestILCode%20Method.md)   
     [GetInstrumentedILMap メソッド](../Topic/ICorDebugILCode2::GetInstrumentedILMap%20Method.md)  
  
-   **イベント トレーシングの変更。** .NET Framework 4.5.2 では、より大きなサーフェイス領域において、アウトプロセスの Windows イベント トレーシング (ETW) に基づくアクティビティ トレーシングができるようになりました。 これにより、アドバンスト パワー マネージメント (APM) ベンダーは、スレッドを越えた個々の要求とアクティビティのコストを正確に追跡する軽量ツールを提供できます。  これらのイベントは、ETW コントローラーで有効にされた場合にのみ発生します。したがって、変更は以前に記述された ETW コードや ETW が無効な状態で実行されるコードには影響しません。  
  
-   **トランザクションの昇格と永続参加リストへの変換**  
  
     [Transaction.PromoteAndEnlistDurable](assetId:///M:System.Transactions.Transaction.PromoteAndEnlistDurable(System.Guid,System.Transactions.IPromotableSinglePhaseNotification,System.Transactions.ISinglePhaseNotification,System.Transactions.EnlistmentOptions)?qualifyHint=True&autoUpgrade=True) は、.NET Framework 4.5.2 および 4.6 に追加された新しい API です。  
  
    ```  
  
    [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
    public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,  
                                              IPromotableSinglePhaseNotification promotableNotification,  
                                              ISinglePhaseNotification enlistmentNotification,  
                                              EnlistmentOptions enlistmentOptions)  
  
    ```  
  
     このメソッドは、以前に [ITransactionPromoter.Promote](assetId:///M:System.Transactions.ITransactionPromoter.Promote?qualifyHint=True&autoUpgrade=True) メソッドへの応答として [Transaction.EnlistPromotableSinglePhase](assetId:///M:System.Transactions.Transaction.EnlistPromotableSinglePhase(System.Transactions.IPromotableSinglePhaseNotification)?qualifyHint=True&autoUpgrade=True) によって作成された参加リストで使うことができます。 これは、`System.Transactions` に対して、トランザクションを MSDTC トランザクションに昇格させ、昇格可能参加リストを永続参加リストに「変換」するように要求します。 このメソッドが正常に終了した後は、[IPromotableSinglePhaseNotification](assetId:///T:System.Transactions.IPromotableSinglePhaseNotification?qualifyHint=False&autoUpgrade=True) インターフェイスが `System.Transactions` によって参照されることはなくなり、今後のすべての通知は提供された [ISinglePhaseNotification](assetId:///T:System.Transactions.ISinglePhaseNotification?qualifyHint=False&autoUpgrade=True) インターフェイスに届きます。 問題の参加リストは、永続参加リストとして機能し、トランザクションのログ記録と復旧をサポートする必要があります。 詳細については、「[Transaction.EnlistDurable](assetId:///M:System.Transactions.Transaction.EnlistDurable(System.Guid,System.Transactions.IEnlistmentNotification,System.Transactions.EnlistmentOptions)?qualifyHint=True&autoUpgrade=True)」をご覧ください。 さらに、参加リストは [ISinglePhaseNotification](assetId:///T:System.Transactions.ISinglePhaseNotification?qualifyHint=False&autoUpgrade=True) をサポートする必要があります。  このメソッドは、[ITransactionPromoter.Promote](assetId:///M:System.Transactions.ITransactionPromoter.Promote?qualifyHint=True&autoUpgrade=True) の呼び出しの処理中に "*のみ*" 呼び出すことができます。 そうでない場合は、[TransactionException](assetId:///T:System.Transactions.TransactionException?qualifyHint=False&autoUpgrade=True) 例外がスローされます。  
  
 [ページのトップへ](#introduction)  
  
<a name="v451"></a>   
## <a name="whats-new-in-the-net-framework-451"></a>.NET Framework 4.5.1 の新機能  
 **2014 年 4 月の更新**:  
  
-   [Visual Studio 2013 更新プログラム 2](http://go.microsoft.com/fwlink/p/?LinkId=393658) には、次のシナリオをサポートするポータブル クラス ライブラリ テンプレートの更新が含まれています。  
  
    -   Windows 8.1、Windows Phone 8.1、および Windows Phone Silverlight 8.1 を対象とするポータブル ライブラリで Windows ランタイム API を使用できます。  
  
    -   Windows 8.1 または Windows Phone 8.1 を対象とする場合、ポータブル ライブラリに XAML (Windows.UI.XAML 型) を含めることができます。 次の XAML テンプレートがサポートされています。空白のページ、リソース ディクショナリ、テンプレート コントロール、およびユーザー コントロール。  
  
    -   Windows 8.1 および Windows Phone 8.1 を対象とするストア アプリで使用するためにポータブル Windows ラインタイム コンポーネント (.winmd ファイル) を作成できます。  
  
    -   ポータブル クラス ライブラリのような Windows ストアまたは Windows Phone ストア クラス ライブラリを再ターゲットできます。  
  
     これらの変更の詳細については、[ポータブル クラス ライブラリ](../Topic/Cross-Platform%20Development%20with%20the%20Portable%20Class%20Library.md)に関するページを参照してください。  
  
-   .NET Framework のコンテンツ セットには、Windows アプリをビルドして配置するためのプリコンパイル テクノロジである .NET Native のドキュメントが含まれます。 .NET Native は、中間言語 (IL) ではなくネイティブ コードへアプリを直接コンパイルすることにより、パフォーマンスを向上させます。 詳しくは、「[.NET ネイティブによるアプリのコンパイル](../Topic/Compiling%20Apps%20with%20.NET%20Native.md)」をご覧ください。  
  
-   [.NET Framework Reference Source](http://referencesource.microsoft.com/) で、新しい参照エクスペリエンスと強化された機能が提供されます。 これにより、.NET Frameworkのソース コードをオンラインで参照したり、[リファレンスをダウンロード](http://referencesource.microsoft.com/download.html)してオフラインで表示したりできます。さらに、デバック中にソース (パッチや更新を含む) をステップ実行できます。 詳細については、ブログ記事「[A new look for .NET Reference Source (.NET Reference Source の新しい外観)](http://blogs.msdn.com/b/dotnet/archive/2014/02/24/a-new-look-for-net-reference-source.aspx)」を参照してください。  
  
 .NET Framework 4.5.1 のコア機能の新機能と機能強化には次が含まれます。  
  
-   アセンブリの自動バインディング リダイレクト。 Visual Studio 2013 以降では、アプリまたはそのコンポーネントが同じアセンブリの複数バージョンを参照している場合、.NET Framework 4.5.1 を対象とするアプリのコンパイル時に、バインディング リダイレクトをアプリ構成ファイルに追加できます。 また、.NET Framework の以前のバージョンを対象とするプロジェクトで、この機能を有効にすることもできます。 詳しくは、「[方法: 自動バインディング リダイレクトを有効/無効にする](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Binding%20Redirection.md)」をご覧ください。  
  
-   開発者がサーバーおよびクラウド アプリケーションのパフォーマンスを向上するために役立つ診断情報を収集する機能。 詳細については、[EventSource](assetId:///T:System.Diagnostics.Tracing.EventSource?qualifyHint=False&autoUpgrade=True) クラスの [WriteEventWithRelatedActivityId](assetId:///M:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId(System.Int32,System.Guid,System.Object[])?qualifyHint=False&autoUpgrade=True) メソッドと [WriteEventWithRelatedActivityIdCore](assetId:///M:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore(System.Int32,System.Guid*,System.Int32,System.Diagnostics.Tracing.EventSource.EventData*)?qualifyHint=False&autoUpgrade=True) メソッドをご覧ください。  
  
-   ガベージ コレクション中に大きなオブジェクト ヒープ (LOH) を圧縮する機能。 詳細については、[GCSettings.LargeObjectHeapCompactionMode](assetId:///P:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?qualifyHint=True&autoUpgrade=True) プロパティをご覧ください。  
  
-   その他のパフォーマンス向上 (ASP.NET アプリの中断、マルチコア JIT の改良、.NET Framework 更新後のアプリ起動時間の短縮など)。 詳細については、ブログ記事「[.NET Framework 4.5.1 announcement](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx)」(.NET Framework 4.5.1 についてのお知らせ) および「[ASP.NET app suspend](http://blogs.msdn.com/b/dotnet/archive/2013/10/09/asp-net-app-suspend-responsive-shared-net-web-hosting.aspx)」 (ASP.NET アプリケーションの中断) を参照してください。  
  
 Windows フォームの機能強化には次が含まれます。  
  
-   Windows フォーム コントロールでのサイズ変更。 アプリのアプリケーション構成ファイル (app.config) 内のエントリで有効にすることにより、システム DIP 設定を使用してコントロールのコンポーネント (例: プロパティ グリッドに表示されるアイコン) をサイズ変更できます。 現在、この機能は次の Windows フォーム コントロールでサポートされています。  
  
     [PropertyGrid](assetId:///T:System.Windows.Forms.PropertyGrid?qualifyHint=False&autoUpgrade=True)   
     [TreeView](assetId:///T:System.Windows.Forms.TreeView?qualifyHint=False&autoUpgrade=True)   
     [DataGridView](assetId:///T:System.Windows.Forms.DataGridView?qualifyHint=False&autoUpgrade=True) の一部 (サポートされている追加コントロールについては、「[4.5.2 の新機能](#v452)」をご覧ください)  
  
     この機能を有効にするには、構成ファイル (app.config) に新しい \<appSettings> 要素を追加し、`EnableWindowsFormsHighDpiAutoResizing` 要素を `true` に設定します。  
  
    ```  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
    ```  
  
 Visual Studio 2013 で .NET Framework アプリをデバッグするときの改善点は次のとおりです。  
  
-   Visual Studio デバッガーの戻り値。 Visual Studio 2013 でマネージ アプリをデバッグする場合、メソッドの戻り値の型と値が [自動変数] ウィンドウに表示されます。 デスクトップ アプリ、Windows ストア アプリ、Windows Phone アプリについて、この情報を使用できます。 詳細については、MSDN ライブラリの「[メソッド呼び出しの戻り値の調査](http://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f\(v=vs.120\).aspx)」を参照してください。  
  
-   64 ビット アプリのエディット コンティニュ。 Visual Studio 2013 では、デスクトップ、Windows ストア、Windows Phone 用の 64 ビット マネージ アプリについて、エディット コンティニュ機能がサポートされています。 既存の制限は、32 ビット アプリと 64 ビット アプリの両方でまだ有効です (「[Supported Code Changes (C#)](http://msdn.microsoft.com/library/ms164927\(v=vs.120\).aspx)」(サポートされているコードの変更 (C#)) の記事の最後のセクションを参照してください)。  
  
-   非同期対応のデバッグ。 Visual Studio 2013 で非同期アプリを簡単にデバッグするために、呼び出し履歴には、非同期プログラミングをサポートするためにコンパイラに用意されているインフラストラクチャ コード、および論理上の親フレーム内のチェーンが表示されません。これにより、論理的なプログラムの実行をよりわかりやすく行うことができます。 [タスク] ウィンドウが [並列タスク] ウィンドウに代わって使用され、特定のブレークポイントに関連するタスクが表示されます。また、現在アクティブなタスクやアプリでスケジュールされているタスクなども表示されます。 この機能については、「[.NET Framework 4.5.1 announcement](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx)」(.NET Framework 4.5.1 についてのお知らせ) の「Async-aware debugging」(非同期対応のデバッグ) セクションを参照してください。  
  
-   Windows ランタイム コンポーネント向けのより適切な例外処理のサポート。 Windows 8.1 では、言語の種類に関係なく、Windows ストア アプリから発生する例外には、例外を発生させたエラーに関する情報が保持されます。 この機能については、「[.NET Framework 4.5.1 announcement](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx)」(.NET Framework 4.5.1 についてのお知らせ) の「Windows Store app development」(Windows ストア アプリ開発) のセクションを参照してください。  
  
 Visual Studio 2013 以降では、[Mpgo.exe (マネージ プロファイル ガイド付き最適化ツール)](../Topic/Mpgo.exe%20\(Managed%20Profile%20Guided%20Optimization%20Tool\).md) を使って、Windows 8.x ストア アプリとデスクトップ アプリを最適化することができます。  
  
 ASP.NET 4.5.1 の新機能については、ASP.NET サイトの「[ASP.NET 4.5.1 and Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094)」(ASP.NET 4.5.1 および Visual Studio 2013) を参照してください。  
  
 [ページのトップへ](#introduction)  
  
<a name="core"></a>   
## <a name="whats-new-in-the-net-framework-45"></a>.NET Framework 4.5 の新機能  
  
### <a name="core-new-features-and-improvements"></a>コア機能の新機能と機能強化  
  
-   配置時に .NET Framework 4 アプリケーションを検出して終了することにより、システムの再起動を減らす機能。 「[.NET Framework 4.5 のインストール中のシステム再起動の削減](../Topic/Reducing%20System%20Restarts%20During%20.NET%20Framework%204.5%20Installations.md)」をご覧ください。  
  
-   64 ビット プラットフォームでの 2 ギガバイト (GB) を超える配列のサポート。 この機能は、アプリケーション構成ファイルで有効にすることができます。 「[\<gcAllowVeryLargeObjects> 要素](../Topic/%3CgcAllowVeryLargeObjects%3E%20Element.md)」も参照してください。オブジェクト サイズと配列サイズに関する他の制限も記載されています。  
  
-   サーバーのガベージ コレクションをバックグラウンドで行うことにより、パフォーマンスを改善します。 .NET Framework 4.5 でサーバーのガベージ コレクションを使うと、バックグラウンド ガベージ コレクションが自動的に有効になります。 「[Fundamentals of Garbage Collection](../Topic/Fundamentals%20of%20Garbage%20Collection.md)」(ガベージ コレクションの基礎) トピックの「バックグラウンド サーバー ガベージ コレクション」というセクションをご覧ください。  
  
-   マルチコア プロセッサでオプションで使用できるバックグラウンドの Just-in-time (JIT) コンパイルを使用すると、アプリケーションのパフォーマンスが向上します。 「[ProfileOptimization](assetId:///T:System.Runtime.ProfileOptimization?qualifyHint=False&autoUpgrade=True)」をご覧ください。  
  
-   正規表現エンジンがタイムアウトする前に、正規表現の解決を試みる時間に制限を設ける機能。 [Regex.MatchTimeout](assetId:///P:System.Text.RegularExpressions.Regex.MatchTimeout?qualifyHint=True&autoUpgrade=True) プロパティをご覧ください。  
  
-   アプリケーション ドメインの既定のカルチャを定義する機能。 [CultureInfo](assetId:///T:System.Globalization.CultureInfo?qualifyHint=False&autoUpgrade=True) クラスをご覧ください。  
  
-   Unicode UTF-16 エンコードのコンソール サポート。 [Console](assetId:///T:System.Console?qualifyHint=False&autoUpgrade=True) クラスをご覧ください。  
  
-   カルチャに従った文字列の順序のバージョン指定と比較データのサポート。 [SortVersion](assetId:///T:System.Globalization.SortVersion?qualifyHint=False&autoUpgrade=True) クラスをご覧ください。  
  
-   リソースを取得するときのパフォーマンスを改善します。 「[リソースのパッケージ化と配置](../Topic/Packaging%20and%20Deploying%20Resources%20in%20Desktop%20Apps.md)」を参照してください。  
  
-   Zip 圧縮の機能強化により、圧縮ファイルのサイズが小さくなりました。 [System.IO.Compression](assetId:///N:System.IO.Compression?qualifyHint=True&autoUpgrade=True) 名前空間をご覧ください。  
  
-   [CustomReflectionContext](assetId:///T:System.Reflection.Context.CustomReflectionContext?qualifyHint=False&autoUpgrade=True) クラスを使って、既定のリフレクションの動作をオーバーライドするリフレクション コンテキストをカスタマイズできる機能。  
  
-   [System.Globalization.IdnMapping](assetId:///T:System.Globalization.IdnMapping?qualifyHint=True&autoUpgrade=True) クラスを Windows 8 で使った場合の IDNA (Internationalized Domain Names in Applications) 規格の 2008 バージョンのサポート。  
  
-   オペレーティング システムへの文字列比較の処理代行。.NET Framework を Windows 8 で使ったときに、Unicode 6.0 が実装されます。 他のプラットフォームで実行されている場合、.NET Framework には、Unicode 5.x. を実装する独自の文字列比較データが含まれています。 [String](assetId:///T:System.String?qualifyHint=False&autoUpgrade=True) クラスおよび [SortVersion](assetId:///T:System.Globalization.SortVersion?qualifyHint=False&autoUpgrade=True) クラスの備考セクションをご覧ください。  
  
-   アプリケーション ドメインごとに文字列のハッシュ コードを計算する機能。 「[\<UseRandomizedStringHashAlgorithm> 要素](../Topic/%3CUseRandomizedStringHashAlgorithm%3E%20Element.md)」をご覧ください。  
  
-   [Type](assetId:///T:System.Type?qualifyHint=False&autoUpgrade=True) クラスと [TypeInfo](assetId:///T:System.Reflection.TypeInfo?qualifyHint=False&autoUpgrade=True) クラスで、タイプ リフレクションのサポートが分割されました。 「[Reflection in the .NET Framework for Windows Store Apps](../Topic/Reflection%20in%20the%20.NET%20Framework%20for%20Windows%20Store%20Apps.md)」(Windows ストア アプリのための .NET Framework のリフレクション) をご覧ください。  
  
### <a name="managed-extensibility-framework-mef"></a>MEF (Managed Extensibility Framework)  
 .NET Framework 4.5 では、MEF (Managed Extensibility Framework) に次の新機能が用意されています。  
  
-   ジェネリック型のサポート。  
  
-   属性ではなく命名規則に基づいてパーツを作成できるようにする、規則ベースのプログラミング モデル。  
  
-   複数のスコープ。  
  
-   Windows 8.x ストア アプリを作成するときに使うことができる MEF のサブセット。 このサブセットは、[ダウンロード可能パッケージ](http://go.microsoft.com/fwlink/?LinkId=256238)として NuGet ギャラリーから入手できます。 パッケージをインストールするには、Visual Studio でプロジェクトを開き、**[プロジェクト]** メニューの **[NuGet パッケージの管理]** をクリックし、`Microsoft.Composition` パッケージをオンラインで検索します。  
  
 詳しくは、「[Managed Extensibility Framework (MEF)](../Topic/Managed%20Extensibility%20Framework%20\(MEF\).md)」を参照してください。  
  
### <a name="asynchronous-file-operations"></a>非同期のファイル操作  
 .NET Framework 4.5 では、新しい非同期機能が C# および Visual Basic 言語に追加されました。 これらの機能は、非同期操作を実行するためのタスク ベースのモデルを追加します。 この新しいモデルを使用するには、I/O クラスで非同期メソッドを使用します。 「[非同期ファイル I/O](../Topic/Asynchronous%20File%20I-O.md)」を参照してください。  
  
<a name="tools"></a>   
### <a name="tools"></a>ツール  
 .NET Framework 4.5 では、リソース ファイル ジェネレーター (Resgen.exe) を使うと、.NET Framework アセンブリに埋め込まれた .resources ファイルから Windows 8.x ストア アプリ用の .resw ファイルを作成することができます。 詳しくは、「[Resgen.exe (リソース ファイル ジェネレーター)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md)」をご覧ください。  
  
 マネージ プロファイル ガイド付き最適化ツール (Mpgo.exe) を使用すると、ネイティブ イメージ アセンブリを最適化することによって、アプリケーションの起動時間、メモリの使用率 (ワーキング セットのサイズ)、およびスループットを向上させることができます。 このコマンド ライン ツールは、ネイティブ イメージ アプリケーション アセンブリ用のプロファイル データを生成します。 「[Mpgo.exe (マネージ プロファイル ガイド付き最適化ツール)](../Topic/Mpgo.exe%20\(Managed%20Profile%20Guided%20Optimization%20Tool\).md)」をご覧ください。 Visual Studio 2013 以降では、Windows 8.x ストア アプリおよびデスクトップ アプリを最適化するために、Mpgo.exe を使うことができます。  
  
<a name="parallel"></a>   
### <a name="parallel-computing"></a>並列コンピューティング  
 .NET Framework 4.5 では、並列計算用にいくつかの新機能と機能強化が提供されています。 パフォーマンスの向上、コントロールの強化、非同期プログラミングのサポートの改善、新しいデータフロー ライブラリ、並列デバッグとパフォーマンス分析のためのサポートの強化などが挙げられます。 ブログ「Parallel Programming with .NET」(.NET での並列プログラミング) の記事「[What’s New for Parallelism in .NET 4.5](http://go.microsoft.com/fwlink/?LinkId=235061)」(.NET 4.5 での並列処理の新機能) を参照してください。  
  
<a name="web"></a>   
### <a name="web"></a>Web  
 ASP.NET 4.5 および 4.5.1 では、Web フォーム モデルのバインディング、WebSocket のサポート、非同期ハンドラー、パフォーマンスの向上などの多くの機能が追加されています。 詳細については、次のリソースを参照してください。  
  
-   MSDN ライブラリの「[ASP.NET 4.5 および Visual Studio 2012](../Topic/ASP.NET%20Core%20and%20Visual%20Studio%202015.md)」。  
  
-   ASP.NET のサイトの [ASP.NET 4.5.1 および Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094)に関するページ。  
  
<a name="networking"></a>   
### <a name="networking"></a>ネットワーク  
 .NET Framework 4.5 は、HTTP アプリケーションに新しいプログラミング インターフェイスを提供します。 詳細については、新しい [System.Net.Http](assetId:///N:System.Net.Http?qualifyHint=True&autoUpgrade=True) 名前空間と [System.Net.Http.Headers](assetId:///N:System.Net.Http.Headers?qualifyHint=True&autoUpgrade=True) 名前空間をご覧ください。  
  
 既存の [HttpListener](assetId:///T:System.Net.HttpListener?qualifyHint=False&autoUpgrade=True) と関連クラスを使って WebSocket 接続を受け入れ、やり取りするための新しいプログラミング インターフェイスのサポートも含まれています。 詳細については、新しい [System.Net.WebSockets](assetId:///N:System.Net.WebSockets?qualifyHint=False&autoUpgrade=True) 名前空間と [HttpListener](assetId:///T:System.Net.HttpListener?qualifyHint=False&autoUpgrade=True) クラスをご覧ください。  
  
 また .NET Framework 4.5 には、次のネットワークの機能強化が含まれています。  
  
-   RFC 準拠の URI サポート。 詳細については、[Uri](assetId:///T:System.Uri?qualifyHint=False&autoUpgrade=True) および関連クラスをご覧ください。  
  
-   国際化ドメイン名 (IDN: Internationalized Domain Name) による解析のサポート。 詳細については、[Uri](assetId:///T:System.Uri?qualifyHint=False&autoUpgrade=True) および関連クラスをご覧ください。  
  
-   電子メール アドレスの国際化 (EAI) のサポート。 詳細については、[System.Net.Mail](assetId:///N:System.Net.Mail?qualifyHint=False&autoUpgrade=True) 名前空間をご覧ください。  
  
-   強化された IPv6 サポート。 詳細については、[System.Net.NetworkInformation](assetId:///N:System.Net.NetworkInformation?qualifyHint=False&autoUpgrade=True) 名前空間をご覧ください。  
  
-   デュアル モードのソケットのサポート。 詳細については、[Socket](assetId:///T:System.Net.Sockets.Socket?qualifyHint=False&autoUpgrade=True) クラスと [TcpListener](assetId:///T:System.Net.Sockets.TcpListener?qualifyHint=False&autoUpgrade=True) クラスをご覧ください。  
  
<a name="client"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 .NET Framework 4.5 では、WPF (Windows Presentation Foundation) の次の領域の機能が変更および強化されています。  
  
-   クイック アクセス ツール バー、アプリケーション メニューおよびタブをホストするリボン ユーザー インターフェイスを実装できる新しい [Ribbon](assetId:///T:System.Windows.Controls.Ribbon.Ribbon?qualifyHint=False&autoUpgrade=True) コントロール。  
  
-   同期および非同期のデータ検証をサポートする新しい [INotifyDataErrorInfo](assetId:///T:System.ComponentModel.INotifyDataErrorInfo?qualifyHint=False&autoUpgrade=True) インターフェイス。  
  
-   [VirtualizingPanel](assetId:///T:System.Windows.Controls.VirtualizingPanel?qualifyHint=False&autoUpgrade=True) クラスと [Dispatcher](assetId:///T:System.Windows.Threading.Dispatcher?qualifyHint=False&autoUpgrade=True) クラスの新機能。  
  
-   グループ化された大量のデータを表示するときに、非 UI スレッドのコレクションにアクセスすることによってパフォーマンスを向上。  
  
-   静的プロパティへのデータ バインディング、[ICustomTypeProvider](assetId:///T:System.Reflection.ICustomTypeProvider?qualifyHint=False&autoUpgrade=True) インターフェイスを実装するカスタム型へのデータ バインディング、およびバインディング式からのデータ バインディング情報の取得。  
  
-   値の変更に伴うデータの再配置 (ライブ形成)。  
  
-   項目コンテナーのデータ コンテキストを切断するかどうかをチェックする機能。  
  
-   プロパティの変更とデータ ソースの更新までの経過時間を設定する機能。  
  
-   弱いイベント パターン実装時のサポートの強化。 また、イベントでマークアップ拡張機能を使用することもできるようになりました。  
  
<a name="windows_communication_foundation"></a>   
### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
 .NET Framework 4.5 では、Windows Communication Foundation (WCF) アプリケーションの記述と保守を簡単にするため、次の機能が追加されました。  
  
-   生成された構成ファイルの簡略化。  
  
-   コントラクト優先開発のサポート。  
  
-   ASP.NET 互換モードをより簡単に構成できる機能。  
  
-   既定のトランスポート プロパティ値に変更を加え、設定しなければならない可能性を低減しました。  
  
-   [XmlDictionaryReaderQuotas](assetId:///T:System.Xml.XmlDictionaryReaderQuotas?qualifyHint=False&autoUpgrade=True) クラスを更新して、XML ディクショナリ リーダーのクォータを手動で構成する手間を省けるようにしました。  
  
-   ビルド処理の一部として Visual Studio による WCF 構成ファイルを検証することで、アプリケーションを実行する前に構成エラーを検出できます。  
  
-   新しい非同期ストリーミングのサポート。  
  
-   Internet Information Services (IIS) での HTTPS 上のエンドポイントを公開しやすくする新しい HTTPS プロトコル マッピング。  
  
-   `?singleWSDL` をサービス URL に追加して 1 つの WSDL ドキュメントのメタデータを生成する機能。  
  
-   TCP トランスポートと同様のパフォーマンス特性を持つポート 80 と 443 で真の双方向通信を可能にする Websockets のサポート。  
  
-   コード内の構成サービスのサポート。  
  
-   XML エディターのツール ヒント。  
  
-   [ChannelFactory](assetId:///T:System.ServiceModel.ChannelFactory?qualifyHint=False&autoUpgrade=True) キャッシュのサポート。  
  
-   バイナリ エンコーダーの圧縮サポート。  
  
-   開発者が「ファイア アンド フォーゲット (撃ち放し)」メッセージングを使用するサービスを作成できるようにする UDP トランスポートのサポート。 クライアントは、サービスにメッセージを送信しますが、サービスからの応答を期待しません。  
  
-   HTTP トランスポートとトランスポート セキュリティを使用したときに、単一の WCF エンドポイントで複数の認証モードをサポートする機能。  
  
-   国際化ドメイン名 (IDN: Internationalized Domain Name) を使用する WCF サービスのサポート。  
  
 詳細については、「[Windows Communication Foundation 4.5 の新機能](http://go.microsoft.com/fwlink/?LinkId=228173)」を参照してください。  
  
<a name="windows_workflow_foundation"></a>   
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)  
 .NET Framework 4.5 では、次に示すようないくつかの新しい機能が Windows Workflow Foundation (WF) に追加されました。  
  
-   最初に .NET Framework 4.0.1 ([.NET Framework 4 Platform Update 1](http://go.microsoft.com/fwlink/?LinkID=215092)) の一部として導入された、ステート マシンのワークフロー。 この更新プログラムには、開発者がステート マシン ワークフローを作成できるようにする新しいクラスとアクティビティが複数含まれていました。 .NET Framework 4.5 では、これらのクラスとアクティビティが、次を含むように更新されました。  
  
    -   状態でブレークポイントを設定する機能。  
  
    -   ワークフロー デザイナーで遷移をコピーして貼り付ける機能。  
  
    -   共有されるトリガーの遷移作成のデザイナー サポート。  
  
    -   [StateMachine](assetId:///T:System.Activities.Statements.StateMachine?qualifyHint=False&autoUpgrade=True)、[State](assetId:///T:System.Activities.Statements.State?qualifyHint=False&autoUpgrade=True)、[Transition](assetId:///T:System.Activities.Statements.Transition?qualifyHint=False&autoUpgrade=True) などのようにステート マシン ワークフローを作成する機能。  
  
-   次のようなワークフロー デザイナーの機能が強化されました。  
  
    -   **[クイック検索]** や **[フォルダーを指定して検索]** など、Visual Studio で強化されたワークフロー検索機能。  
  
    -   2 番目の子アクティビティがコンテナー アクティビティに追加されたときに、自動的にシーケンス アクティビティを作成し、両方のアクティビティをシーケンス アクティビティに含める機能。  
  
    -   スクロール バーを使用せずに変更されるワークフローの表示部分を変更できるようにするパン サポート。  
  
    -   ツリー スタイルのアウトライン ビューでワークフローのコンポーネントを表示し、**[ドキュメント アウトライン]** ビューでコンポーネントを選択できるようにする新しい **[ドキュメント アウトライン]** ビュー。  
  
    -   アクティビティに注釈を追加できる機能。  
  
    -   ワークフロー デザイナーでアクティビティ デリゲートを定義および使用する機能。  
  
    -   ステート マシンのアクティビティと遷移、およびフローチャート ワークフローの自動接続と自動挿入。  
  
-   ワークフローのビュー状態情報を XAML ファイルの 1 つの要素に保管して、ビュー状態情報を簡単に見つけ、編集できるようにします。  
  
-   子アクティビティの永続化を防ぐ NoPersistScope コンテナー アクティビティ。  
  
-   C# 式のサポート:   
  
    -   Visual Basic を使用するワークフロー プロジェクトは、Visual Basic 式を使用し、C# ワークフロー プロジェクトは C# 式を使用します。  
  
    -   Visual Studio 2010 で作成され、Visual Basic 式が使用されている C# ワークフロー プロジェクトは、C# 式を使用する C# ワークフロー プロジェクトと互換性があります。  
  
-   バージョン管理機能の強化  
  
    -   永続化されたワークフロー インスタンスとワークフロー定義間のマッピングを提供する新しい [WorkflowIdentity](assetId:///T:System.Activities.WorkflowIdentity?qualifyHint=False&autoUpgrade=True) クラス。  
  
    -   [WorkflowServiceHost](assetId:///T:System.ServiceModel.Activities.WorkflowServiceHost?qualifyHint=False&autoUpgrade=True) を含む同じホスト内の複数のワークフローのバージョンの並列実行。  
  
    -   動的更新プログラムで、永続化されたワークフロー インスタンスの定義を変更する機能。  
  
-   既存のサービス コントラクトに合わせて自動的にアクティビティを生成するサポートが提供されるコントラクト優先のワークフロー サービス開発。  
  
 詳細については、「[.NET 4.5 での Windows Workflow Foundation の新機能](http://go.microsoft.com/fwlink/?LinkId=228176)」を参照してください。  
  
<a name="tailored"></a>   
### <a name="net-for-windows-8x-store-apps"></a>Windows 8.x ストア アプリ用 .NET  
 Windows 8.x ストア アプリは、特定のフォーム ファクターに合わせて設計されており、Windows オペレーティング システムの機能を利用します。 C# または Visual Basic を使って Windows 用の Windows 8.x ストア アプリをビルドするために、.NET Framework 4.5 または 4.5.1 のサブセットを使うことができます。 このサブセットは Windows 8.x ストア アプリ用 .NET と呼ばれ、Windows デベロッパー センターの[概要](http://go.microsoft.com/fwlink/?LinkId=228491)のページで説明されています。  
  
<a name="portable"></a>   
### <a name="portable-class-libraries"></a>ポータブル クラス ライブラリ  
 Visual Studio 2012 (および以降のバージョン) のポータブル クラス ライブラリ プロジェクトを使うと、複数の .NET Framework プラットフォームで動作するマネージ アセンブリを作成してビルドできます。 ポータブル クラス ライブラリ プロジェクトを使って、対象とするプラットフォーム (Windows Phone や Windows 8.x ストア アプリ用 .NET など) を選択します。 プロジェクトで使用できる型およびメンバーは、自動的にこれらのプラットフォーム間で共通の型とメンバーに制限されます。 詳細については、[ポータブル クラス ライブラリ](../Topic/Cross-Platform%20Development%20with%20the%20Portable%20Class%20Library.md)に関するページを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [.NET Framework および OOB リリース](~/docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)   
 [Visual Studio 2013 の新機能 ](http://msdn.microsoft.com/library/bb386063\(v=vs.120\).aspx)   
 [ASP.NET 4.5.1 および Visual Studio 2013 用 Web ツール](http://go.microsoft.com/fwlink/?LinkID=309094)   
 [ASP.NET および Visual Studio for Web](../Topic/ASP.NET%20and%20Visual%20Studio%20for%20Web.md)   
 [Windows Communication Foundation の新機能](http://go.microsoft.com/fwlink/?LinkId=228173)   
 [Windows Workflow Foundation の新機能](http://go.microsoft.com/fwlink/?LinkId=228176)   
 [Visual C++ の新機能](http://msdn.microsoft.com/library/hh409293\(v=vs.120\).aspx)

