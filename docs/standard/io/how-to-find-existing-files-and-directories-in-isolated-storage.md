---
title: "方法 : 分離ストレージ内でファイルおよびディレクトリを検索する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET Framework], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET Framework], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 656c390358b6f6a671cf3ef11ea7be75f897d21c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>方法 : 分離ストレージ内でファイルおよびディレクトリを検索する
分離ストレージ内のディレクトリを検索するには、使用、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType>メソッドです。 このメソッドは、検索パターンを表す文字列を受け取ります。 単一文字 (?) と複数文字 (*) の両方を使用する検索パターンでのワイルドカード文字しますが、名前の最後の部分にワイルドカード文字を含める必要があります。 たとえば、`directory1/*ect*`は有効な検索文字列が`*ect*/directory2`はありません。  
  
 ファイルを検索するには、使用、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType>メソッドです。 適用する検索文字列にワイルドカード文字の制限は、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A>にも適用されます<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>です。  
  
 どちらの方法は、再帰的です。<xref:System.IO.IsolatedStorage.IsolatedStorageFile>クラスはすべてのディレクトリまたはユーザーのストア内のファイルを一覧表示するためのメソッドを指定していません。 ただし、再帰的な方法は、次のコード例に示します。  
  
## <a name="example"></a>例  
 次のコード例は、分離ストアのファイルとディレクトリを作成する方法を示しています。 ユーザー、ドメイン、およびアセンブリの分離されたストアが取得されに最初に、`isoStore`変数。 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A>メソッドを使用して、いくつかの異なるディレクトリを設定し、<xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29>コンス トラクターは、これらのディレクトリにいくつかのファイルを作成します。 コードがの結果をループ処理し、`GetAllDirectories`メソッドです。 このメソッドを使用して<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A>を現在のディレクトリ内のすべてのディレクトリ名を検索します。 これらの名前は、配列に格納し、`GetAllDirectories`呼び出し自体が検出する各ディレクトリに渡します。 その結果、すべてのディレクトリ名は、配列で返されます。 次に、コードを呼び出して、`GetAllFiles`メソッドです。 このメソッドを呼び出す`GetAllDirectories`をすべての名前を調べるには、ディレクトリでは、その後チェック ファイルの各ディレクトリを使用して、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>メソッドです。 ディスプレイの配列では、結果が返されます。  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [分離ストレージ](../../../docs/standard/io/isolated-storage.md)
