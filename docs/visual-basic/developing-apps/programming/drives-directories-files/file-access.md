---
title: Visual Basic におけるファイル アクセス
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- file access
- files [Visual Basic], input and output
- file access, Visual Basic
- files [Visual Basic], I/O
- file I/O classes
- data [Visual Basic], accessing from files
- files [Visual Basic], accessing
- file access, using components
- My.Computer.FileSystem object, accessing files
- I/O [Visual Basic]
- sequential access
ms.assetid: 231533bf-d049-4345-befa-3fb78fe6517d
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2aabea79e3c7a6dabf47647c7e27b072738ba363
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="e655a-102">Visual Basic におけるファイル アクセス</span><span class="sxs-lookup"><span data-stu-id="e655a-102">File Access with Visual Basic</span></span>
<span data-ttu-id="e655a-103">`My.Computer.FileSystem` オブジェクトには、ファイルとフォルダーを操作するツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e655a-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="e655a-104">そのプロパティ、メソッド、イベントを使用すると、ファイルとフォルダーの作成、コピー、移動、調査、削除が可能になります。</span><span class="sxs-lookup"><span data-stu-id="e655a-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="e655a-105">`My.Computer.FileSystem` は、下位互換性のために Visual Basic に用意されているレガシ関数 (`FileOpen`、`FileClose`、`Input`、`InputString`、`LineInput` など) よりもパフォーマンスが優れています。</span><span class="sxs-lookup"><span data-stu-id="e655a-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e655a-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e655a-106">In This Section</span></span>  
 [<span data-ttu-id="e655a-107">ファイルの読み取り</span><span class="sxs-lookup"><span data-stu-id="e655a-107">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 <span data-ttu-id="e655a-108">`My.Computer.FileSystem` オブジェクトを使用したファイルからの読み込みに関するトピックを一覧表示します</span><span class="sxs-lookup"><span data-stu-id="e655a-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="e655a-109">ファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="e655a-109">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 <span data-ttu-id="e655a-110">`My.Computer.FileSystem` オブジェクトを使用したファイルへの書き込みに関するトピックを一覧表示します</span><span class="sxs-lookup"><span data-stu-id="e655a-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="e655a-111">ファイルおよびディレクトリの作成、削除、および移動</span><span class="sxs-lookup"><span data-stu-id="e655a-111">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="e655a-112">`My.Computer.FileSystem` オブジェクトを使用したファイルとフォルダーの作成、コピー、削除、移動に関するトピックを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="e655a-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="e655a-113">TextFieldParser オブジェクトによるテキスト ファイルの解析</span><span class="sxs-lookup"><span data-stu-id="e655a-113">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="e655a-114">`TextFieldReader` を使用して、ログなどのテキスト ファイルを解析する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e655a-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="e655a-115">ファイル エンコーディング</span><span class="sxs-lookup"><span data-stu-id="e655a-115">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 <span data-ttu-id="e655a-116">ファイル エンコーディングとその使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e655a-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="e655a-117">チュートリアル: Visual Basic によるファイルとディレクトリの操作</span><span class="sxs-lookup"><span data-stu-id="e655a-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="e655a-118">ファイルおよびフォルダーに関する情報を報告するユーティリティの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e655a-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="e655a-119">トラブルシューティング : テキスト ファイルの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="e655a-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="e655a-120">テキスト ファイルの読み込みと書き込みで発生する一般的な問題を示し、それぞれの解決策を提案します。</span><span class="sxs-lookup"><span data-stu-id="e655a-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
