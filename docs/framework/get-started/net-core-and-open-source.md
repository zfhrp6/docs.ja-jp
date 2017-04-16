---
title: ".NET Core とオープン ソース | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 6
---
# .NET Core とオープン ソース
.NET Core は、コードを最大限に再使用および共有してプラットフォーム間で移植できるように設計されている、.NET Framework モジュール形式バージョンです。 さらに、.NET Core はオープン ソース化され、コミュニティからの投稿を受け入れる予定です。 このトピックでは .NET Core に関するいくつかの一般的な質問と、このオープン ソース パッケージにアクセスして投稿する方法について取り上げます。  
  
<a name="BKMK_WhatisNETCore"></a>   
## .NET Core とは何ですか?  
 前述のように、.NET Core は、プラットフォーム間で移植できるように設計されているモジュール形式の .NET Framework バージョンです。  
  
 .NET Core は、.NET Framework 全体のサブセットではありますが、ターゲットとするプラットフォームに関係なく、必要とするアプリケーション機能を実装してそのコードを再使用するための主な機能が備わっているため、プラットフォームを超えて移植が可能です。 これまでは、各プラットフォームの .NET バージョンがそれぞれにあり、ローカル ファイルの読み取りなど重要なタスクにおける共有機能が欠けていました。 .NET Core を使用してターゲットとできる Microsoft のプラットフォームには、従来のデスクトップの Windows だけでなく Windows デバイスや携帯電話なども含まれます。 Xamarin などのサードパーティ製のツールを使用すれば、.NET Core は IOS および Android のデバイスにも移植できます。 さらに、.NET Core は、Mac および Linux オペレーティング システムでも間もなく利用可能になる予定で、それらのシステムで Web アプリを実行できるようになります。  
  
 .NET Core は、小規模のアセンブリ パッケージで NuGet を介してリリースされるためモジュール形式となっています。 .NET Core はコア機能のほとんどが含まれる 1 つの大きなアセンブリではなく、中心的な機能が含まれる比較的小さなパッケージとして提供されています。 こうすることで、当社は従来よりも柔軟な開発モデルを提供でき、開発者はアプリとライブラリで必要とする機能を選択できます。 NuGet でリリースされる .NET パッケージの詳細については、「[.NET Framework および特別なリリース](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)」を参照してください。  
  
 .NET Core についてよく寄せられる質問を以下に取り上げます。  
  
### どうすれば .NET Core の利点を最大限に活用できますか?  
 既存のアプリの場合 .NET Core を使用してコードの再使用機能を最大限に生かすには、ポータブル クラス ライブラリ \(PCL\) とユニバーサル アプリ プロジェクトを使用して、プラットフォーム固有のコードからビジネス ロジックを分離するという方法が最善です。 アプリを .NET Core に簡単に移行するには、Model\-View\-Controller \(MVC\) パターンまたはModel View\-ViewModel \(MVVM\) パターンが適切な選択肢となります。  
  
### .NET Core は互換性と配置にどのような影響を及ぼしますか?  
 配置にはいくつかのシナリオがありますが、いずれの場合も簡単に行えます。 この .NET Framework は Windows と共に配布され、現在同様、Microsoft Update を通じて更新される予定です。 ご使用のアプリは、.NET Framework のディスク上の配置に依存する場合もあれば、アプリ パッケージと一緒に配置される .NET アセンブリに依存することもあります。 さらに、バージョン間の互換性は引き続き .NET Framework の最優先事項であるため、ご使用のアプリをコンパイルしたときよりも新しいバージョンのアセンブリでアプリを実行してもそれまでと同じように動作します。  
  
|シナリオ|配置|  
|----------|--------|  
|Windows デスクトップ アプリ、および Windows コンピューター上で実行される ASP.NET アプリ|配置は現在と同じです。 アプリは、サーバーまたはユーザーのコンピューター上にある .NET Framework のインストールに依存します。 .NET Framework がインストールされていない場合、ユーザーはインストールするように求められます。 または、アプリと .NET インストールを結びつけることも可能です。 .NET Framework に含まれていないアセンブリを .NET Core から使用すると、それらのアセンブリが、アプリ パッケージに組み込まれます。 また、同じアプリで 2 つの異なるバージョンの同一のアセンブリを参照している場合、アプリは新しい方のアセンブリにリダイレクトされます。 詳細については、「[アプリ レベルでのアセンブリ バージョンのリダイレクト](../../../docs/framework/configure-apps/redirect-assembly-versions.md#BKMK_Redirectingassemblyversionsattheapplevel)」および「[方法: 自動バインディング リダイレクトを有効\/無効にする](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)」を参照してください。<br /><br /> .NET の配置の詳細については、「[配置ガイド \(開発者向け\)](../../../docs/framework/deployment/deployment-guide-for-developers.md)」を参照してください。|  
|Windows ストアおよび Windows Phone ストアから利用できる Windows アプリ と Windows Phone アプリ|配置は現在と同じで、アプリは、オペレーティング システムに含まれている .NET Framework アセンブリを使用します。 アプリが .NET Framework に含まれていない .NET Core アセンブリでリリースされた機能を使用する場合、そのアセンブリはアプリ パッケージに組み込まれます。 アプリが複数のバージョンの同一アセンブリを参照する場合、アセンブリの新しい方のバージョンをアプリは自動的に使用します。|  
|ASP.NET Core 5.0 アプリ|.NET Core アセンブリはアプリ ローカルです。つまり必須アセンブリはアプリ パッケージによって配置されます。 ASP.NET Core 5.0 の詳細については、「[ASP.NET 5 の概要](http://www.asp.net/vnext/overview/aspnet-vnext/aspnet-5-overview)」を参照してください。|  
|Xamarin ツールでビルドされた他のプラットフォームで実行されるアプリ|現時点では、これらのアプリケーションは、アプリ パッケージに同梱されている効率化された一連の Monoアセンブリとともに配置されます。 これは、オープン ソース化される .NET Core アセンブリが増えると変更される可能性があります。|  
  
<a name="BKMK_NETCoreOpenSourcePackages"></a>   
## .NET Core オープン ソース パッケージ  
 Microsoft は .NET Framework のモジュール化に加えて、.NET Core パッケージを [MIT](https://github.com/dotnet/corefx/blob/master/LICENSE) ライセンスに基づいて [GitHub](https://github.com/) でオープン ソース化しています。 つまり、GitHub にある他のオープン ソース パッケージと同様に、Git リポジトリを複製し、コードを読み取ってコンパイルし、プル要求を送信できます。 Microsoft の品質と互換性への取り組みにより、各プル要求が承諾されるにはその前に慎重に評価されます。 よく寄せられる質問をいくつか以下に記します。  
  
### どのようにすればコードを入手してビルドできますか?  
 .NET Core ソース パッケージは `GitHub` にあり、ソース管理システムとして `Git` を使用してます。 コードにアクセスしてビルドするには、[Git](http://git-scm.com/)、[GitHub](https://github.com/dotnet/corefx)、[Visual Studio](http://msdn.microsoft.com/vstudio/aa718325.aspx) に関する基本的知識がいくらか必要になりますが、以下の手順には、使用を開始するために必要な情報とリンクが提供されています。  
  
 Git と GitHub をセットアップするには、GitHub サイトの「[Git のセットアップ](https://help.github.com/articles/set-up-git/)」を参照してください。  
  
 .NET Framework コードにアクセスするには、当該コードが含まれている Git リポジトリをフォークし、開発用コンピューターに複製する必要があります。 リポジトリに移動して、ブラウザーの右上隅にある \[**フォーク**\] をクリックするとコードのフォークを行えます。 GitHub アプリを使用してまたは GitHub シェルのコマンドラインで、フォークを複製できます。 GitHub シェルでリポジトリを複製するには、次のコマンドを実行します。  
  
```  
git clone https://github.com/dotnet/corefx  
```  
  
 コードをビルドするには、Visual Studio 2013 がインストールされている必要があります。 次に、Visual Studio 2013 でソリューションを開いて F5 を押してビルドするか、開発者コマンド プロンプトを使用してコマンドライン上でビルドできます。 コマンド プロンプトでビルドする場合、開発者コマンド プロンプトを開き、ソース コードを複製したフォルダーに移動します。 その後、次にように入力します。  
  
```  
build.cmd  
  
```  
  
 開発者コマンド プロンプトを表示する方法の詳細については、「[コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)」を参照してください。  
  
### コードを送信するためのガイドラインがありますか?  
 Microsoft がお客様の作業内容をマスター分岐に取りこむ前に、お客様は[投稿者のライセンス契約 \(Contributor License Agreement: CLA\)](https://cla.dotnetfoundation.org/) に署名する必要があります。  
  
 Microsoft は、フォークとプル モデルを使用したコミュニティからの投稿を受け入れています。 コードをフォークして複製し、プル要求を .NET Framework のマスター分岐に送信してくささい。 プル要求の詳細については、「[プル要求の使用法](https://help.github.com/articles/using-pull-requests/)」を参照してください。 プル要求の送信に関するガイドラインの詳細については、「[.NET Core の投稿に関するガイド](https://github.com/dotnet/corefx/wiki/Contributing)」を参照してください。  
  
### 私のプル要求が承諾されなかったのはなぜですか?  
 Microsoft がお客様の要求を拒否する場合、その理由をお伝えしますが、多くの場合、Microsoft がコードの品質と互換性に関して高いコミットメントを維持していることが理由となります。 プル要求が承諾されなかった場合、コーディングのガイドラインに準拠していなかったこと、コード送信のテストが不十分だったこと、API 互換性がなかったことなどが考えられます。 また、コード変更は .NET Framework のロードマップに則したものであるべきです。 コーディングのガイドラインの詳細については、「[.NET Core の投稿に関するガイド](https://github.com/dotnet/corefx/wiki/Contributing)」を参照してください。  
  
## 参照  
 [.NET はオープン ソース](http://blogs.msdn.com/b/dotnet/archive/2014/11/12/net-core-is-open-source.aspx)   
 [.NET オープン ソース Curah](https://curah.microsoft.com/254870/net-core-open-source)   
 [ASP.NET 5 の概要](http://www.asp.net/vnext/overview/aspnet-vnext/aspnet-5-overview)