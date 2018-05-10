---
title: アセンブリとグローバル アセンブリ キャッシュ (C#)
ms.date: 07/20/2015
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
ms.openlocfilehash: 994498525aed3ebb08f2de7926c7adc2d3d95f56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="assemblies-and-the-global-assembly-cache-c"></a>アセンブリとグローバル アセンブリ キャッシュ (C#)
アセンブリは、.NET ベースのアプリケーションの配置、バージョン管理、再利用、アクティベーション スコープ、およびセキュリティ権限の基本単位です。 アセンブリは、実行可能 (.exe) ファイルまたはダイナミック リンク ライブラリ (.dll) ファイルの形を取る、.NET Framework の構成要素です。 それらは、型の実装に関して必要な情報を共通言語ランタイムに提供します。 アセンブリは、機能的な論理的な単位を形成し、連携して動作するように構築された、型とリソースのコレクションと考えることができます。  
  
 アセンブリには、1 つまたは複数のモジュールを含めることができます。 たとえば、大規模なプロジェクトを、複数の開発者が別々のモジュールで作業し、すべてのモジュールをまとめて 1 つのアセンブリを作成するように計画することができます。 モジュールの詳細については、「[方法: マルチファイル アセンブリをビルドする](../../../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)」を参照してください。  
  
 アセンブリには、次の特徴があります。  
  
-   アセンブリは、.exe または .dll ファイルとして実装されます。  
  
-   アセンブリは、グローバル アセンブリ キャッシュに配置することで、アプリケーション間で共有することができます。 グローバル アセンブリ キャッシュに含める前に、アセンブリに厳密な名前を付ける必要があります。 詳細については、「[厳密な名前付きアセンブリ](../../../../../docs/framework/app-domains/strong-named-assemblies.md)」を参照してください。  
  
-   アセンブリは、必要な場合にのみメモリに読み込まれます。 使用されない場合、読み込まれることはありません。 これは、アセンブリを使用すると、大規模なプロジェクト内のリソースを効率的に管理できることを意味します。  
  
-   リフレクションを使用して、アセンブリに関する情報をプログラムによって取得できます。 詳細については、「[リフレクション (C#)](../../../../csharp/programming-guide/concepts/reflection.md)」を参照してください。  
  
-   アセンブリのみを読み込んで検査する場合は、<xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> などのメソッドを使用します。  
  
## <a name="assembly-manifest"></a>アセンブリ マニフェスト  
 すべてのアセンブリの中にあるのが "*アセンブリ マニフェスト*" です。 目次と同じように、アセンブリ マニフェストには次の項目が含まれます。  
  
-   アセンブリの ID (名前とバージョン)。  
  
-   アセンブリを構成するその他すべてのファイルについて記述するファイル テーブル。.exe または .dll ファイルが依存するアセンブリ、ビットマップ、Readme ファイルなどが含まれます。  
  
-   "*アセンブリ参照リスト*"。これはすべての外部依存関係の一覧であり、アプリケーションが必要とする .dll ファイルやその他のファイルで、他の人物が作成している場合があるファイルです。 アセンブリ参照には、グローバルおよびプライベートの両方のオブジェクトへの参照が含まれます。 グローバル オブジェクトは、他のアプリケーションで使用できるグローバル アセンブリ キャッシュ内に存在します。 プライベート オブジェクトは、アプリケーションがインストールされているディレクトリと同じレベルまたはその下のディレクトリ内に存在する必要があります。  
  
 アセンブリには、コンテンツ、バージョン管理、および依存関係に関する情報が含まれているため、C# で作成するアプリケーションが、正常に機能するために Windows のレジストリ値に依存することはありません。 アセンブリは、.dll の競合を減らし、アプリケーションの信頼性を高め、配置を容易にします。 多くの場合、 NET ベースのアプリケーションは、対象のコンピュータにそのファイルをコピーするだけでインストールすることができます。  
  
 詳細については、「[アセンブリ マニフェスト](../../../../../docs/framework/app-domains/assembly-manifest.md)」を参照してください。  
  
## <a name="adding-a-reference-to-an-assembly"></a>アセンブリへの参照の追加  
 アセンブリを使用するには、アセンブリへの参照を追加する必要があります。 次に、[using ディレクティブ](../../../../csharp/language-reference/keywords/using-directive.md)を使用して、使用する項目の名前空間を選択します。 アセンブリが参照されてインポートされた後、名前空間のアクセス可能なすべてのクラス、プロパティ、メソッド、およびのその他のメンバーのコードは、ソース ファイルの一部であるかのようにアプリケーションで使用することができます。  
  
 C# では、1 つのアプリケーションで同じアセンブリの 2 つのバージョンを使用することもできます。 詳細については、「[extern エイリアス](../../../../csharp/language-reference/keywords/extern-alias.md)」を参照してください。  
  
## <a name="creating-an-assembly"></a>アセンブリの作成  
 アプリケーションをコンパイルするには、**[ビルド]** メニューの **[ビルド]** をクリックするか、コマンド ライン コンパイラを使用してコマンド ラインからビルドします。 コマンド ラインからのアセンブリのビルドの詳細については、「[csc.exe を使用したコマンド ラインからのビルド](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。  
  
> [!NOTE]
>  Visual Studio でアセンブリをビルドするには、**[ビルド]** メニューの **[ビルド]** を選択します。  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../../csharp/programming-guide/index.md)  
 [共通言語ランタイムのアセンブリ](../../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [フレンド アセンブリ (C#)](friend-assemblies.md)  
 [方法 : アセンブリを他のアプリケーションと共有する (C#)](how-to-share-an-assembly-with-other-applications.md)  
 [方法: アセンブリを読み込み、アンロードする (C#)](how-to-load-and-unload-assemblies.md)  
 [方法: ファイルがアセンブリであるかどうかを確認する (C#)](how-to-determine-if-a-file-is-an-assembly.md)  
 [方法: コマンド ラインを使用してアセンブリを作成および使用する (C#)](how-to-create-and-use-assemblies-using-the-command-line.md)  
 [チュートリアル: Visual Studio でマネージ アセンブリからの型を埋め込む (C#)](walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [チュートリアル: Visual Studio で Microsoft Office アセンブリからの型情報を埋め込む (C#)](walkthrough-embedding-type-information-from-microsoft-office-assemblies.md)
