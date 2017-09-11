---
title: "C# 6.0 のドラフト言語仕様"
ms.date: 2017-07-01
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: reference
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, specification
- what's new [C#], language specification
- Visual C#, C# language specification
- language specification [C#]
ms.assetid: e5d5a5cc-636b-4bff-b9c8-a8edc6207c22
caps.latest.revision: 46
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
ms.translationtype: HT
ms.sourcegitcommit: dbc7f6ad4e6ddd30b3c808840420335a0c0155ad
ms.openlocfilehash: 904b0f5bf99ed133eb505f65faaa63ca99053f5a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/23/2017

---
# <a name="c-60-draft-language-specification"></a><span data-ttu-id="14c94-102">C# 6.0 のドラフト言語仕様</span><span class="sxs-lookup"><span data-stu-id="14c94-102">C# 6.0 draft Language Specification</span></span>
<span data-ttu-id="14c94-103">C# 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。</span><span class="sxs-lookup"><span data-stu-id="14c94-103">The C# Language Specification is the definitive source for C# syntax and usage.</span></span> <span data-ttu-id="14c94-104">この仕様には、Visual C# のドキュメントで取り上げられていない多数の点を含め、C# 言語に関する詳細情報が全面的に網羅されています。</span><span class="sxs-lookup"><span data-stu-id="14c94-104">This specification contains detailed information about all aspects of the language, including many points that the documentation for Visual C# doesn't cover.</span></span>

<span data-ttu-id="14c94-105">この仕様のバージョン 5.0 を [Microsoft ダウンロード センター](http://www.microsoft.com/download/details.aspx?id=7029)からダウンロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="14c94-105">You can download version 5.0 of this specification from the [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=7029).</span></span> <span data-ttu-id="14c94-106">Visual Studio 2015 をインストールした場合は、そのコンピューターの Program Files (x86)/Microsoft Visual Studio 14.0/VC#/Specifications/1033 フォルダーにも仕様が含まれています。</span><span class="sxs-lookup"><span data-stu-id="14c94-106">If you've installed Visual Studio 2015, you can also find the specification on your computer in the Program Files (x86)/Microsoft Visual Studio 14.0/VC#/Specifications/1033 folder.</span></span> <span data-ttu-id="14c94-107">別のバージョンの Visual Studio をインストールした場合、または英語以外の言語で Visual Studio をインストールした場合は、適切なパスに変更してください。</span><span class="sxs-lookup"><span data-stu-id="14c94-107">If you have another version of Visual Studio installed or if you installed Visual Studio in a language other than English, change the path as appropriate.</span></span>

<span data-ttu-id="14c94-108">バージョン 6.0 の仕様は標準として承認されていません。</span><span class="sxs-lookup"><span data-stu-id="14c94-108">Version 6.0 of the specification has not been approved as a standard.</span></span> <span data-ttu-id="14c94-109">このサイトには、[*ドラフト*の C# 6.0 仕様](../../../../_csharplang/spec/lexical-structure.md)が含まれています。</span><span class="sxs-lookup"><span data-stu-id="14c94-109">This site contains the [*draft* C# 6.0 specification](../../../../_csharplang/spec/lexical-structure.md).</span></span> <span data-ttu-id="14c94-110">[dotnet/csharplang GitHub レポジトリ](https://github.com/dotnet/csharplang/blob/master/spec/README.md)に含まれているマークダウン ファイルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="14c94-110">It is built from the markdown files contained in [the dotnet/csharplang GitHub repository](https://github.com/dotnet/csharplang/blob/master/spec/README.md).</span></span>

<span data-ttu-id="14c94-111">ドラフト仕様の問題は [dotnet/csharplang](https://github.com/dotnet/csharplang/issues) リポジトリで作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14c94-111">Issues on the draft specification should be created in the [dotnet/csharplang](https://github.com/dotnet/csharplang/issues) repository.</span></span> <span data-ttu-id="14c94-112">見つけたエラーを修正したい場合は、同じレポジトリに[プル要求](https://github.com/dotnet/csharplang/pulls)を送信できます。</span><span class="sxs-lookup"><span data-stu-id="14c94-112">Or, if you are interested in fixing any errors you find, you may submit a [Pull Request](https://github.com/dotnet/csharplang/pulls) to the same repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="14c94-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="14c94-113">See Also</span></span>  
 [<span data-ttu-id="14c94-114">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="14c94-114">C# Reference</span></span>](../../language-reference/index.md)  
 [<span data-ttu-id="14c94-115">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="14c94-115">C# Programming Guide</span></span>](../../programming-guide/index.md)

>[!div class="step-by-step"]
[<span data-ttu-id="14c94-116">次へ</span><span class="sxs-lookup"><span data-stu-id="14c94-116">Next</span></span>](../../../../_csharplang/spec/lexical-structure.md)

