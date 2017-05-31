---
title: "-linkresource (C# コンパイラ オプション) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /linkresource
dev_langs:
- CSharp
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: d9a3bc4dc4b51d6170c67f9d2f95b6805497b31c
ms.contentlocale: ja-jp
ms.lasthandoff: 05/10/2017

---
# <a name="linkresource-c-compiler-options"></a>/linkresource (C# コンパイラ オプション)
.NET Framework のリソースへのリンクを出力ファイルに作成します。 リソース ファイルが出力ファイルに追加されることはありません。 これに対し、[/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) オプションはリソース ファイルを出力ファイルに埋め込みます。  
  
## <a name="syntax"></a>構文  
  
```console  
/linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 アセンブリからリンクする .NET Framework のリソース ファイル。  
  
 `identifier` (省略可能)  
 リソースの論理名。リソースを読み込むために使われる名前です。 既定値は、ファイルの名前です。  
  
 `accessibility-modifier` (省略可能)  
 リソースのアクセシビリティ。パブリックまたはプライベートです。 既定値はパブリックです。  
  
## <a name="remarks"></a>コメント  
 既定では、リンクされたリソースは、C# コンパイラで作成されるときにアセンブリ内でパブリックになります。 リソースをプライベートにするには、アクセシビリティ修飾子として `private` を指定します。 `public` または `private` 以外の他の修飾子は許可されません。  
  
 **/linkresource** には、**/target:module** 以外のいずれかの [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) オプションが必要です。  
  
 `filename` が [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) や開発環境などで作成された .NET Framework リソース ファイルである場合は、<xref:System.Resources> 名前空間のメンバーを使ってそのファイルにアクセスできます。 詳細については、「<xref:System.Resources.ResourceManager?displayProperty=fullName>」を参照してください。 それ以外のすべてのリソースについては、<xref:System.Reflection.Assembly> クラスの `GetManifestResource`* メソッドを使って、実行時にリソースにアクセスします。  
  
 `filename` で指定するファイルはどのような形式でもかまいません。 たとえば、ネイティブ DLL をアセンブリの一部にすることで、グローバル アセンブリ キャッシュにインストールして、アセンブリ内のマネージ コードからアクセスできるようにすることができます。 以下の例の 2 番目で、その方法を示します。 同じことをアセンブリ リンカーで行うことができます。 以下の例の 3 番目で、その方法を示します。 詳しくは、「[Al.exe (アセンブリ リンカー)](https://msdn.microsoft.com/library/c405shex)」および「[アセンブリとグローバル アセンブリ キャッシュの使用](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)」をご覧ください。  
  
 **/linkres** は **/linkresource** の省略形式です。  
  
 このコンパイラ オプションは Visual Studio では使用できず、プログラムで変更することはできません。  
  
## <a name="example"></a>例  
 `in.cs` をコンパイルして、リソース ファイル `rf.resource` にリンクします。  
  
```console  
csc /linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>例  
 `A.cs` をコンパイルして DLL を作成し、ネイティブ DLL N.dll にリンクして、出力をグローバル アセンブリ キャッシュ (GAC) に配置します。 この例では、A.dll と N.dll の両方を GAC に置きます。  
  
```console  
csc /linkresource:N.dll /t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>例  
 この例では、前の例と同じことを行いますが、アセンブリ リンカー オプションを使います。  
  
```console  
csc /t:module A.cs  
al /out:A.dll A.netmodule /link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [Al.exe (アセンブリ リンカー)](https://msdn.microsoft.com/library/c405shex)   
 [アセンブリとグローバル アセンブリ キャッシュの使用](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)   
 [NIB 方法: プロジェクト プロパティと構成設定を変更する](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
