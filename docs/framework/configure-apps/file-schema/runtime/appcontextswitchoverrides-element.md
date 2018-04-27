---
title: '&lt;AppContextSwitchOverrides&gt;要素'
ms.custom: ''
ms.date: 04/19/2018
ms.prod: .net-framework
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 146416a9872a8444316c2e4a754067b82030a81d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ltappcontextswitchoverridesgt-element"></a>&lt;AppContextSwitchOverrides&gt;要素
<xref:System.AppContext> クラスで使用される、新機能に対するオプトアウト メカニズムを指定するスイッチを 1 つまたは複数定義します。  
  
 \<configuration>  
 \<ランタイム >  
\<AppContextSwitchOverrides>  
  
## <a name="syntax"></a>構文  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`value`|必須の属性です。<br /><br /> 1 つまたは複数のスイッチ名と関連付けられたブール値を定義します。|  
  
### <a name="value-attribute"></a>属性の値  
  
|[値]|説明|  
|-----------|-----------------|  
|"name=value"|値と共に定義済みのスイッチの名前 (`true`または`false`)。 複数のスイッチの名前/値ペアをセミコロンで区切られます (「;」) です。 .NET Framework でサポートされている定義済みのスイッチ名の一覧は、「解説」セクションを参照してください。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>コメント  
 .NET Framework 4.6 以降で、`<AppContextSwitchOverrides>`構成ファイル内の要素は、自社のアプリでの新機能を利用できます、ライブラリの以前のバージョンとの互換性を維持するかを判断するために API の呼び出し元を許可します。 たとえば、ライブラリの 2 つのバージョン間の API の動作が変更された場合、`<AppContextSwitchOverrides>`要素は、新しい機能をサポートするバージョンのライブラリに新しい動作から除外するには、その API の呼び出し元を許可します。 アプリの .NET framework Api を呼び出すこと、`<AppContextSwitchOverrides>`要素は呼び出し元がアプリを含む .NET Framework のバージョンで、アプリが実行されている場合に、新しい機能を選択する .NET Framework の以前のバージョンを対象にもできます機能します。  
  
 `value`の属性、`<AppContextSwitchOverrides>`要素は、1 つまたは複数のセミコロンで区切られた名前/値ペアで構成される 1 つの文字列で構成されます。  それぞれの名前は、互換性スイッチを識別し、対応する値はブール値 (`true`または`false`) スイッチが設定されているかどうかを示すです。 スイッチは、既定では、 `false`、およびライブラリは、新しい機能を提供します。 スイッチが設定されている場合のみ以前の機能を提供する (つまり、その値は`true`)。 これにより、既存の API の新しい機能しないことを以前の動作に依存している呼び出し元を許可するときに新しい動作を提供するライブラリです。  
  
 .NET Framework には、次のスイッチがサポートされています。  
  
|スイッチの名前|説明|導入されました。|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Windows Presentation Foundation がコントロールのレイアウトのレガシなアルゴリズムを使用するかどうかを制御します。 詳細については、「[軽減策: WPF レイアウト](~/docs/framework/migration-guide/mitigation-wpf-layout.md)」を参照してください。|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|PackageDigitalSignatureManager によってパッケージのパーツの署名に使用する既定のアルゴリズムは SHA1 または SHA256 かどうかを制御します。|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|設定すると`false`FIPS が有効にすると、Visual Studio で XAML ベースのワークフロー プロジェクトのデバッグを許可します。 これがないと、 <xref:System.NullReferenceException> System.Activities アセンブリ内のメソッドの呼び出しでがスローされます。|.NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|デバッガー内のワークフロー インスタンスのチェックサムが MD5 または SHA1 を使用するかどうかを制御します。 | .NET Framework 4.7|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|コントロールかどうか、<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType>メソッドが例外をスロー時に、<xref:System.Drawing.Icon>オブジェクトに PNG フレーム。 詳細については、「[軽減策: Icon オブジェクトの PNG フレーム](~/docs/framework/migration-guide/mitigation-png-frames-in-icon-objects.md)」を参照してください。|.NET Framework 4.6|  
|`Switch.System.Drawing.Printing.`</br>`OptimizePrintPreview`|コントロールかどうかのパフォーマンス、<xref:System.Windows.Forms.PrintPreviewDialog>ネットワーク プリンターに適しています。 詳細については、次を参照してください。 [PrintPreviewDialog コントロールの概要](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md)です。|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|非同期操作が呼び出し元のスレッドのコンテキストからフローしないかどうかを制御します。 詳細については、次を参照してください。 [CurrentCulture、CurrentUICulture のフローのタスクにわたって](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks)です。|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|コントロールかどうか、<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType>メソッドは、要求の種類と最後の DNS エントリのみを一致させようとしています。 詳細については、「[軽減策: X509CertificateClaimSet.FindClaims メソッド](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md)」を参照してください。|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|変更可能なオブジェクトを返す AuthorizationContext.Empty を許可するかどうかを制御します。|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|コントロールかどうかを超えるパス`MAX_PATH`(260) スロー、<xref:System.IO.PathTooLongException>です。 詳細については、次を参照してください。[長いパスをサポート](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support)です。|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|バック スラッシュを使用して ("\\")、スラッシュではなく (「/」) でのパス区切り記号として、<xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType>プロパティです。 詳細については、次を参照してください。[軽減策: ZipArchiveEntry.FullName パス区切り](~/docs/framework/migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md)です。|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|オペレーティング システムの例外はで作成されたバック グラウンド スレッドでスローされるかどうかを制御<xref:System.IO.Ports.SerialPort>ストリーム プロセスを終了します。|.NET Framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|レガシ パスの正規化を使用してによって URI パスがサポートされているかどうかを制御、<xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType>と<xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>メソッドです。 詳細については、次を参照してください。[軽減策: パスの正規化](~/docs/framework/migration-guide/mitigation-path-normalization.md)と[軽減策: パス コロン チェック](~/docs/framework/migration-guide/mitigation-path-colon-checks.md)です。|.NET Framework 4.6.2|  
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|等値比較をテストするかどうかを制御、<xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType>を持つ 1 つのオブジェクトのプロパティ、 <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> 2 番目のオブジェクトのプロパティです。 詳細については、次を参照してください。 [MemberDescriptor.Equals の実装が正しくない](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals)です。|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|証明書の拡張キー使用法 (EKU) のオブジェクト識別子 (OID) の検証を無効にします。 EKU (拡張キー使用法) 拡張は、キーを使用するアプリケーションを示すオブジェクト識別子 (OID) の集まりです。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|SCH_SEND_AUX_RECORD の使用を無効にして TLS1.0 ブラウザー悪用に対して SSL や TLS (BEAST) の対策を無効にします。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|コントロールかどうか、<xref:System.Net.ServicePointManager?displayProperty=nameWithType>と<xref:System.Net.Security.SslStream?displayProperty=nameWithType>クラスは、SSL 3.0 プロトコルを使用できます。 詳細については、「[軽減策: TLS プロトコル](~/docs/framework/migration-guide/mitigation-tls-protocols.md)」を参照してください。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|システム標準の TLS バージョン Tls12、Tls、Tls11、既定値に戻すことを無効にします。|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|SslStream TLS サーバー側のアラートを無効にします。|.NET Framework 4.7|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |コントロールかどうか、 [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) ECMAScript V6 と V8 スタンダードに基づくいくつかの制御文字をシリアル化します。 詳細については、「[軽減策: DataContractJsonSerializer での制御文字のシリアル化](Mitigation:%20Serialization%20of%20Control%20Characters%20with%20the%20DataContractJsonSerializer.md)」を参照してください。| .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|コントロールかどうか、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>のタイム ゾーンの調整が複数または単一の調整のみをサポートしています。 場合`true`を使用して、<xref:System.TimeZoneInfo>をシリアル化する型および日付と時刻のデータを逆シリアル化以外の場合は、<xref:System.TimeZone>型で、複数の調整規則をサポートしていません。|.NET Framework 4.6.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|コントロールかどうか、<xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType>コンス トラクターは、新しいオブジェクトを設定<xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType>既存のオブジェクト参照を持つプロパティです。 詳細については、「[軽減策: ClaimsIdentity コンストラクター](~/docs/framework/migration-guide/mitigation-claimsidentity-constructor.md)」を参照してください。|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|コントロールかどうかを再使用しようとすると、<xref:System.Security.Cryptography.AesCryptoServiceProvider>復号化をスロー、<xref:System.Security.Cryptography.CryptographicException>です。 詳細については、AesCryptoServiceProvider 復号化は、再利用可能な transform](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform) を参照してください。|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|コントロールかどうかの値、 [CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle)プロパティは、 [IntPtr](xref:System.IntPtr)ことを表しますウィンドウのメモリ位置を処理するかどうか、ウィンドウ ハンドル (HWND)。 詳細については、「[Mitigation: CspParameters.ParentWindowHandle Expects an HWND](Mitigation:%20CspParameters.ParentWindowHandle%20Expects%20an%20HWND.md)」 (軽減策: CspParameters.ParentWindowHandle で HWND を受け取る) を参照してください。 |.NET Framework 4.7|   
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|一部の SignedCMS 操作の既定値は SHA1 または SHA256 かどうかを判断します。 |.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|一部の SignedXML 操作の既定値は SHA1 または SHA256 かどうかを判断します。 |.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|決定するかどうか、`TransportWithMessageCredential`セキュリティ モードでは、符号なしとメッセージを"to"ヘッダー。 これは、オプトイン スイッチです。 詳細については、次を参照してください。 [、.NET Framework 4.6.1 におけるランタイムの変更](https://msdn.microsoft.com/library/mt592686.aspx#WCF)です。|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|コントロールかどうか、<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>コンス トラクターをスロー、<xref:System.ArgumentException>場合は、要素の 1 つ`null`です。|.NET Framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|CSG キー記憶域プロバイダーが例外をスローすると証明書の X509 の使用を試みているかどうかを判断します。 詳細については、次を参照してください。 [WCF トランスポート セキュリティは、CNG を使用して格納されている証明書をサポートしている](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng)です。|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|自己ホスト型サービスと、HTTP トランスポートを使用している場合は、この値を設定`true`により、アプリケーションの追加を無視する WCF、`Connection: close`要求の応答ヘッダーにヘッダー。 この値を設定`false`追加できるように、`Connection: close`応答ヘッダーにヘッダー。 応答が送信された後に、要求、ソケットを閉じるときに発生します。|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|同時実行の 1 つのスレッドに再入可能サービスのインスタンスを制限することに起因するデッドロックを処理します。|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|と共に`Switch.System.Net.DontEnableSchUseStrongCrypto`、TLS 1.1 および TLS 1.2 に WCF メッセージ セキュリティを使用するかどうかを指定します。|.NET Framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|値`false`プロトコルを選択するオペレーティング システムを許可する既定の構成を設定します。 値`true`使用可能な最も高いプロトコルを既定値に設定します。 (以前のバージョンのフレームワークの分岐をサービスにも使用可能)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|署名アルゴリズムの MSMQ メッセージが WCF の既定のメッセージが SHA1 または SHA256 かどうかを判断します。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|WCF が、SHA1 または SHA256 ハッシュを使用して名前付きパイプのランダムな名前を生成するかどうかを制御します。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|スローするかどうかを制御する[NullReferenceException](xref:System.NullReferenceException)例外メッセージが null の場合。|.NET Framework 4.7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|呼び出し元にサービスの開始時にスローされる例外を反映するかどうかを制御、<xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>メソッドです。|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Windows Presentation Foundation は、古いアルゴリズムを適用するかどうかを判断 (`true`) または新しいアルゴリズム (`false`) に領域の割り当てで\*-列です。 詳細については、「[Mitigation: Grid Control's Space Allocation to Star-columns](Mitigation:%20Grid%20Control's%20Space%20Allocation%20to%20Star-columns.md)」 (軽減策: グリッド コントロールの *-column へのディスク領域の割り当て) を参照してください。 |.NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|コントロールの選択範囲を発生させる前に、選択した値のプロパティの値を更新、セレクターまたはタブが常にして制御するかどうかは、イベントを変更します。|.NET Framework 4.7.1|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|DPI の変更がシステムごとに発生するかどうかを判断 (値の`false`) またはモニターごとに (値の`true`)。|.NET Framework 4.6.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|により、カスタム コードを止めた<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>例外をスローせず、メッセージを安全にフィルター処理の実装時に、<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>メソッドが呼び出されます。 詳細については、[「軽減策: カスタムの IMessageFilter.PreFilterMessage 実装」](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)を参照してください。|.NET Framework 4.6.1|  
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|省略可能なのかどうかを決定`WM_POINTER`-に基づいてタッチ/スタイラス スタックが WPF アプリケーションで有効にします。 詳細については、次を参照してください[軽減策: ポインターに基づくタッチとスタイラス入力のサポート。](Mitigation:%20Pointer-based%20Touch%20and%20Stylus%20Support.md) | 
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|レガシかどうかを制御[NullReferenceException](xref:System.NullReferenceException)をより具体的には、例外の原因を示す例外ではなくがスローされます (など、 [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException)または、 [FileNotFoundException](xref:System.IO.FileNotFoundException)です。 処理に依存するコードで使用するもので、 [NullReferenceException](xref:System.NullReferenceException)です。 | .NET Framework 4.7 |
|`Switch.UseLegacyAccessibilityFeatures`|コントロールは、ユーザー補助機能を以降、.NET Framework 4.7.1 で使用可能かどうかが有効または無効になっています。 | .NET Framework 4.7.1 |
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|XSD スキーマ検証によって、複合キーに空のキー シーケンスが無視するかどうかを制御します。 詳細については、次を参照してください。[軽減策: XML スキーマ検証](~/docs/framework/migration-guide/mitigation-xml-schema-validation.md)です。|.NET Framework 4.6|  
  
> [!NOTE]
>  追加する代わりに、`AppContextSwitchOverrides`アプリケーション構成ファイルに要素を設定することも、スイッチ プログラムで呼び出すことによって、 `static` (C# の場合) または`Shared`(Visual Basic) の<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>メソッドです。  
  
 ライブラリ開発者は、それらのライブラリの以降のバージョンで導入された変更された機能しないことを呼び出し元を許可するカスタムのスイッチも定義できます。 詳細については、<xref:System.AppContext> クラスを参照してください。  
  
## <a name="example"></a>例  
 次の例では、`AppContextSwitchOverrides`要素で、1 つのアプリケーションの互換性スイッチを定義する`Switch.System.Globalization.NoAsyncCurrentCulture`、妨げているカルチャ非同期メソッド呼び出し内のスレッド間を移動します。  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 次の例では、`AppContextSwitchOverrides`要素で 2 つのアプリケーションの互換性スイッチを定義する`Switch.System.Globalization.NoAsyncCurrentCulture`と`Switch.System.IO.BlockLongPaths`です。 2 つの名前/値ペアをセミコロンで区切ってことに注意してください。  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.AppContext?displayProperty=nameWithType>  
 [\<ランタイム > 要素](runtime-element.md)  
 [\<configuration> 要素](../configuration-element.md)
