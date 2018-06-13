---
title: アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)
ms.date: 07/20/2015
ms.assetid: fcf78ff1-f1ab-4a5d-b6d8-00d2046b6c80
ms.openlocfilehash: 6d1692d6b62e1f1f3a8f979d3de242003f034ed5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644252"
---
# <a name="assemblies-and-the-global-assembly-cache-visual-basic"></a>アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)
アセンブリは、.NET ベースのアプリケーションの配置、バージョン管理、再利用、アクティベーション スコープ、およびセキュリティ権限の基本単位です。 アセンブリは、実行可能 (.exe) ファイルまたはダイナミック リンク ライブラリ (.dll) ファイルの形を取る、.NET Framework の構成要素です。 それらは、型の実装に関して必要な情報を共通言語ランタイムに提供します。 アセンブリは、機能的な論理的な単位を形成し、連携して動作するように構築された、型とリソースのコレクションと考えることができます。  
  
 アセンブリには、1 つまたは複数のモジュールを含めることができます。 たとえば、大規模なプロジェクトを、複数の開発者が別々のモジュールで作業し、すべてのモジュールをまとめて 1 つのアセンブリを作成するように計画することができます。 モジュールの詳細については、「[方法: マルチファイル アセンブリをビルドする](../../../../framework/app-domains/how-to-build-a-multifile-assembly.md)」を参照してください。  
  
 アセンブリには、次の特徴があります。  
  
-   アセンブリは、.exe または .dll ファイルとして実装されます。  
  
-   アセンブリは、グローバル アセンブリ キャッシュに配置することで、アプリケーション間で共有することができます。 グローバル アセンブリ キャッシュに含める前に、アセンブリに厳密な名前を付ける必要があります。 詳細については、「[厳密な名前付きアセンブリ](../../../../framework/app-domains/strong-named-assemblies.md)」を参照してください。  
  
-   アセンブリは、必要な場合にのみメモリに読み込まれます。 使用されない場合、読み込まれることはありません。 これは、アセンブリを使用すると、大規模なプロジェクト内のリソースを効率的に管理できることを意味します。  
  
-   リフレクションを使用して、アセンブリに関する情報をプログラムによって取得できます。 詳細については、「[リフレクション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)」を参照してください。  
  
-   アセンブリのみを読み込んで検査する場合は、<xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> などのメソッドを使用します。  
  
## <a name="assembly-manifest"></a>アセンブリ マニフェスト  
 すべてのアセンブリの中にあるのが "*アセンブリ マニフェスト*" です。 目次と同じように、アセンブリ マニフェストには次の項目が含まれます。  
  
-   アセンブリの ID (名前とバージョン)。  
  
-   アセンブリを構成するその他すべてのファイルについて記述するファイル テーブル.exe または .dll ファイルが依存するアセンブリ、ビットマップ、Readme ファイルなどが含まれます。  
  
-   "*アセンブリ参照リスト*"。これはすべての外部依存関係の一覧であり、アプリケーションが必要とする .dll ファイルやその他のファイルで、他の人物が作成している場合があるファイルです。 アセンブリ参照には、グローバルおよびプライベートの両方のオブジェクトへの参照が含まれます。 グローバル オブジェクトは、System32 ディレクトリのような、他のアプリケーションが使用できるグローバル アセンブリ キャッシュ内に存在します。 <xref:Microsoft.VisualBasic?displayProperty=nameWithType> 名前空間は、グローバル アセンブリ キャッシュ内のアセンブリの例です。 プライベート オブジェクトは、アプリケーションがインストールされているディレクトリと同じレベルまたはその下のディレクトリ内に存在する必要があります。  
  
 アセンブリには、コンテンツ、バージョン管理、および依存関係に関する情報が含まれているため、Visual Basic で作成するアプリケーションは、正常に機能するために Windows のレジストリ値に依存するはありません。 アセンブリは、.dll の競合を減らし、アプリケーションの信頼性を高め、配置を容易にします。 多くの場合、 NET ベースのアプリケーションは、対象のコンピュータにそのファイルをコピーするだけでインストールすることができます。  
  
 詳細については、「[アセンブリ マニフェスト](../../../../framework/app-domains/assembly-manifest.md)」を参照してください。  
  
## <a name="adding-a-reference-to-an-assembly"></a>アセンブリへの参照の追加  
 アセンブリを使用するには、アセンブリへの参照を追加する必要があります。 次に、[Imports ステートメント](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)を使用して、使用する項目の名前空間を選択します。 アセンブリが参照されてインポートされた後、名前空間のアクセス可能なすべてのクラス、プロパティ、メソッド、およびのその他のメンバーのコードは、ソース ファイルの一部であるかのようにアプリケーションで使用することができます。  
  
## <a name="creating-an-assembly"></a>アセンブリの作成  
 アプリケーションをコンパイルするには、コマンド ライン コンパイラを使用してコマンドラインからビルドします。 コマンドラインからのアセンブリのビルドの詳細については、「[コマンドラインからのビルド](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」を参照してください。  
  
> [!NOTE]
>  Visual Studio でアセンブリをビルドするには、**[ビルド]** メニューの **[ビルド]** を選択します。  
  
## <a name="see-also"></a>関連項目  
 [共通言語ランタイムのアセンブリ](../../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [フレンド アセンブリ (Visual Basic)](friend-assemblies.md)  
 [方法: アセンブリ共有する他のアプリケーション (Visual Basic)](how-to-share-an-assembly-with-other-applications.md)  
 [方法: ロードおよびアンロード アセンブリ (Visual Basic)](how-to-load-and-unload-assemblies.md)  
 [方法: がかどうか、ファイル アセンブリ (Visual Basic)](how-to-determine-if-a-file-is-an-assembly.md)  
 [方法: を作成し、コマンドライン (Visual Basic) を使用してアセンブリを使用します。](how-to-create-and-use-assemblies-using-the-command-line.md)  
 [チュートリアル: Visual Studio (Visual Basic) でのマネージ アセンブリから型の埋め込み](walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [チュートリアル: Visual Studio で Microsoft Office アセンブリからの型情報を埋め込む (Visual Basic)](walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-vs.md)
