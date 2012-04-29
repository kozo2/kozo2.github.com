---
layout: post
title: "Cytoscape2.8.3のビルドとMagic Trackpadでのパン操作"
description: ""
category: 
tags: [Cytoscape, Mac]
---
{% include JB/setup %}

Cytoscape2.8.3では今までMacのMagic Trackpad環境ではやりにくかったnetworkのpanが
「Command keyを押しながらdragすることで可能になった」、とcore developerの大野さんからtwitter
で伺ったので早速ためしてみました。

## Cytoscape2.8.3のbuild

Cytoscape2.8.3でないと機能しない、かつまだdmg fileが配布されていないとのことなので自分でbuildします。

### repositoryのcheckout

下記commandでsource codeをcheckoutします

    svn co http://chianti.ucsd.edu/svn/cytoscape/trunk cytoscape

### mavenの設定とbuild

下記commandでmavenの環境変数の設定とbuildを行います。

    export MAVEN_OPTS="-Xmx1024m"
    cd cytoscape/distribution
    mvn install

## Cytoscape2.8.3の起動とCommand keyを用いたpan操作

これで distribution/target/cytoscape-2.8.3-SNAPSHOT-null/cytoscape-2.8.3-SNAPSHOT の下にCytoscape2.8.3ができあがっていると思います。あとは下記commandでCytoscape2.8.3を起動後に適当なnetworkを作成し、MacのCommand keyを押しながら任意の箇所をdragしてみてください。pan操作が手軽に行えるようになっているかと思います。

    cd target/cytoscape-2.8.3-SNAPSHOT-null/cytoscape-2.8.3-SNAPSHOT
    sh cytoscape.sh
