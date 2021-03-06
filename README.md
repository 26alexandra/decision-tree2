# decision-tree2{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {
    "collapsed": false
   },
   "source": [
    "# Was ist ein Entscheidungsbaum\n",
    "\n",
    "Der Entscheidungsbaum soll die Entscheidungsfindung erleichtern und bildlich darstellen.\n",
    "\n",
    "### Definition:\n",
    "\n",
    "Ein hierarchisch angeordneter Such-Baum zur Darstellung von Entscheidungsregeln. Die Pfade des Baumes stellen Regeln dar. Entscheidungsbäume können binäre und numerische Daten behandeln\n",
    "\n",
    "#### Beispiel\n",
    "\n",
    "Entscheidung: Steht eine Frau oder ein Mann vor mir?\n",
    "\n",
    "**Kriterien:\n",
    "\n",
    "•\tTrägt ein Rock (S)\n",
    "•\tHat langes Haar (H)\n",
    "•\tHat hohe Stimme (V)\n",
    "\n",
    "Folgendes konnte Beobachtet werden:\n",
    "\n",
    "S\t H\t V\t   sex\n",
    "j\t j\t j\t    F\n",
    "j\t j\t n\t    F\n",
    "j\t n\t j\t    F\n",
    "j\t n\t n\t    M\n",
    "n\t j\t j\t    M\n",
    "n\t n\t j\t    M\n",
    "\n",
    "Mittels dieser Daten kann gelernt werden\n",
    "\n",
    "#### Aufbau eines Baums\n",
    "\n",
    "Der Entscheidungsbaum besteht aus\n",
    "•\tKnoten mit Attributen\n",
    "•\tFäden mit Bedeutung der Attribute\n",
    "•\tBlättern mit Antworten \n",
    "\n",
    "#### Optimaler Baum:\n",
    "**Was ist Optimal?** \n",
    "→ Bereits mit erster Frage  großen Schritt zur Lösung des Problems machen. Somit sollte man nicht mit unwichtigen Fragen beginnen. Als erstes Kernfragen!\n",
    "Diese Vorgehensweise wird uns schneller zur Lösung führen, da wir weniger Fragen stellen müssen. Die Information geht dabei nicht verloren und wird sogar erhöht. \n",
    "\n",
    "**Entropie:**\n",
    "\n",
    "Wir besitzen die Menge aus N Elementen. Es gibt eine Eigenschaft S, diese kann zwei Zustände annehmen (Deutung, kann auch mehr als zwei sein). \n",
    "Die Menge M dieser Elemente besitz die Eigenschaft S=’x’. Die restlichen N-M besitzen die Eigenschaft ‚y’. Dann gilt:\n",
    "\n",
    "**H(S)= - ∑pi log2(pi) = -(m/n + log2(m/n) + (m-n)/n * log2((m-n)/n))**\n",
    "\n",
    "Pi → weißt drauf hin dass  S alle Eigenschaften annehmen kann\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {
    "collapsed": false
   },
   "outputs": [
    {
     "data": {
      "image/jpeg": "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\nIgCIiAIiIAiIgCIiAIiID//Z\n",
      "text/html": [
       "\n",
       "        <iframe\n",
       "            width=\"400\"\n",
       "            height=\"300\"\n",
       "            src=\"https://www.youtube.com/embed/R4OlXb9aTvQ\"\n",
       "            frameborder=\"0\"\n",
       "            allowfullscreen\n",
       "        ></iframe>\n",
       "        "
      ],
      "text/plain": [
       "<IPython.lib.display.YouTubeVideo at 0x10e518ef0>"
      ]
     },
     "execution_count": 3,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "from IPython.display import YouTubeVideo\n",
    "YouTubeVideo('R4OlXb9aTvQ')"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### Beispiel:\n",
    "\n",
    "Das deutsche Alphabet hat 26 Buchstaben. Dabei kommt jeder Buchstabe mit gleicher Wahrscheinlichkeit vor (1/26). Die Eigenschaft S ist z.B. Vokal des Buchstabens\n",
    "Somit gilt:\n",
    "**H(S) = - (5/26 * log2(5/26) + (21/26*log2(21/26))=0.706**\n",
    "\n",
    "Bedeutet auch das um ein Buchstabe aufzunehmen bei so einer Wahrscheinlichkeit und Reihenfolge werden          Bit gebraucht.\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Hier kann die Frage Aufkommen**\n",
    "→ Was ist wenn die Buchstaben nicht bei einer gleichen Wahrscheinlichkeit vorkommen?\n",
    "\n",
    "Diese frage kann mit Bais Klassifikation beantwortet werden.\n",
    "\n",
    "Informationsfluss des Attributs\n",
    "\n",
    "Beispiel:\n",
    "\n",
    "Angenommen wir haben ein Atrribut Q dieser kann zwei Bedeutungen annehmen.\n",
    "Dann wir die Information-gain unterschiedlich entrotopisch ausgeprägt.\n",
    "\n",
    "G(Q) =H(S) – p1H1(S) – p2H2(S)\n",
    "\n",
    "P1= Anteil der Daten mit erster Bedeutung\n",
    "Qp2 = Anteil mit zweiter Bedeutung\n",
    "Hi entropie\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Jetzt können wir den Informationsfluss bewerten, das kann mit dem Gini-Index (information gain) berechnet werden: \n",
    "\n",
    "Aus dem vorherigen Beispiel:\n",
    "\n",
    "Eigenschaft\t\tInfo-gain\n",
    "\n",
    "Rock\t(S)\t\t  0.553\n",
    "Lange Haare\t(H)\t  0.057\n",
    "Hohe Stimme\t(V)   0\n",
    "\n",
    "Das bedeutet, dass die Eigenschaft Rock beinhaltet die meiste Information um die Frage welches Geschlecht die Person hat zu beantworten.\n",
    "Die Eigenschaft Stimme dagegen liefert überhaupt kein Information. Das liegt daran, dass wir genau zwei Männer und zwei Frauen die hohe Stimme besitzen und einen Mann und eine frau mit tiefer stimme. Somit kann hier nur Aufgrund dieser Beobachtungen noch keine Aussage getroffen werden. \n",
    "\n",
    "Da das Attribut Rock die größte Entropie hat werden wir damit beginnen unseren baum aufzubauen.\n",
    "Wenn wir alle Daten mit Attribut Rock uns anschauen, \n",
    "\n",
    "S\tH\tV\tsex\n",
    "Ja\tja\tja\tF\n",
    "Ja\tja\tnein\tF\n",
    "Ja\tnein\tja\tF\n",
    "Ja\tnein \tnein\tM\n",
    "\n",
    "Hier können wir vier Fälle betrachten. Um das nächste Attribut auszuwählen muss wieder die gain berechnet werden. In diesem Fall ist es aber auch so schon ersichtlich, dass die gain gleich ist (0.216). Somit ist es egal für welches Attribut wir uns entscheiden.\n",
    "Wir wählen Haare\n",
    "\n",
    "S=y, H=y\t\t\t\t\tS=y, H=n\n",
    "S\tH\tV\tsex\t\t\tS\tH\tV\tsex\n",
    "Ja\tja\tja\tF\t\t\tja\tnein\tja\tF\n",
    "Ja\tja\tnein\tF\t\t\tja\tnein\tnein\tM\n",
    "\n",
    "Das heisst, im Fall von H=y → Frau\n",
    "\t        Im Fall von H=n→ neue Analyse\n",
    "S\tH\tV\tsex\n",
    "Nein\tja\tja\tM\n",
    "Nein\tnein\tja\tM\n",
    "\n",
    "Leider ist es in diesem Fall nicht eindeutig → keine Unterscheidung mehr möglich.\t\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {
    "collapsed": false
   },
   "outputs": [],
   "source": [
    "# Klassifikation des Baums\n",
    "from sklearn import datasets\n",
    "from sklearn import metrics\n",
    "from sklearn.tree import DecisionTreeClassifier\n",
    " \n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {
    "collapsed": false
   },
   "outputs": [],
   "source": [
    "# einlesen der iris Daten\n",
    "dataset = datasets.load_iris()\n",
    "\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {
    "collapsed": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "DecisionTreeClassifier(class_weight=None, criterion='gini', max_depth=None,\n",
      "            max_features=None, max_leaf_nodes=None,\n",
      "            min_impurity_split=1e-07, min_samples_leaf=1,\n",
      "            min_samples_split=2, min_weight_fraction_leaf=0.0,\n",
      "            presort=False, random_state=None, splitter='best')\n"
     ]
    }
   ],
   "source": [
    "# Prozess der Einstellung von CART zur Auswahl der Daten\n",
    "model = DecisionTreeClassifier()\n",
    "model.fit(dataset.data, dataset.target)\n",
    "print(model)\n",
    "\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "# Ermittlung\n",
    "expected = dataset.target\n",
    "predicted = model.predict(dataset.data)\n",
    "\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {
    "collapsed": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "             precision    recall  f1-score   support\n",
      "\n",
      "          0       1.00      1.00      1.00        50\n",
      "          1       1.00      1.00      1.00        50\n",
      "          2       1.00      1.00      1.00        50\n",
      "\n",
      "avg / total       1.00      1.00      1.00       150\n",
      "\n",
      "[[50  0  0]\n",
      " [ 0 50  0]\n",
      " [ 0  0 50]]\n"
     ]
    }
   ],
   "source": [
    "# Wie gut wird ermittelt \n",
    "print(metrics.classification_report(expected, predicted))\n",
    "print(metrics.confusion_matrix(expected, predicted))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "metadata": {
    "collapsed": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "{'trägt ein Rock': {0: 'M', 1: {'lange Haare': {0: {'hohe Stimme': {0: 'M', 1: 'F'}}, 1: 'F'}}}}\n"
     ]
    }
   ],
   "source": [
    "from math import log\n",
    "import operator\n",
    "\n",
    "def createDataSet():\n",
    "    dataSet = [[1, 1, 1, 'F'],\n",
    "               [1, 1, 0, 'F'],\n",
    "               [1, 0, 1, 'F'],\n",
    "               [1, 0, 0, 'M'],\n",
    "               [0, 1, 1, 'M'],\n",
    "               [0, 0, 1, 'M'],]\n",
    "    labels = ['trägt ein Rock', 'lange Haare', 'hohe Stimme']\n",
    "    # diskrete Werte\n",
    "    return dataSet, labels\n",
    "\n",
    "def calcShannonEnt(dataSet):\n",
    "    numEntries = len(dataSet)\n",
    "    labelCounts = {}\n",
    "    for featVec in dataSet:  # the the number of unique elements and their occurance\n",
    "        currentLabel = featVec[-1]\n",
    "        if currentLabel not in labelCounts.keys(): labelCounts[currentLabel] = 0\n",
    "        labelCounts[currentLabel] += 1\n",
    "    shannonEnt = 0.0\n",
    "    for key in labelCounts:\n",
    "        prob = float(labelCounts[key]) / numEntries\n",
    "        shannonEnt -= prob * log(prob, 2)  # log base 2\n",
    "    return shannonEnt\n",
    "\n",
    "\n",
    "def splitDataSet(dataSet, axis, value):\n",
    "    retDataSet = []\n",
    "    for featVec in dataSet:\n",
    "        if featVec[axis] == value:\n",
    "            reducedFeatVec = featVec[:axis]  # chop out axis used for splitting\n",
    "            reducedFeatVec.extend(featVec[axis + 1:])\n",
    "            retDataSet.append(reducedFeatVec)\n",
    "    return retDataSet\n",
    "\n",
    "\n",
    "def chooseBestFeatureToSplit(dataSet):\n",
    "    numFeatures = len(dataSet[0]) - 1  # the last column is used for the labels\n",
    "    baseEntropy = calcShannonEnt(dataSet)\n",
    "    bestInfoGain = 0.0;\n",
    "    bestFeature = -1\n",
    "    for i in range(numFeatures):  # iterate over all the features\n",
    "        featList = [example[i] for example in dataSet]  # create a list of all the examples of this feature\n",
    "        uniqueVals = set(featList)  # get a set of unique values\n",
    "        newEntropy = 0.0\n",
    "        for value in uniqueVals:\n",
    "            subDataSet = splitDataSet(dataSet, i, value)\n",
    "            prob = len(subDataSet) / float(len(dataSet))\n",
    "            newEntropy += prob * calcShannonEnt(subDataSet)\n",
    "\n",
    "\n",
    "        infoGain = baseEntropy - newEntropy  # calculate the info gain; ie reduction in entropy\n",
    "   \n",
    "        if (infoGain > bestInfoGain):  # compare this to the best gain so far\n",
    "            bestInfoGain = infoGain  # if better than current best, set to best\n",
    "            bestFeature = i\n",
    "    return bestFeature  # returns an integer\n",
    "\n",
    "\n",
    "def majorityCnt(classList):\n",
    "    classCount = {}\n",
    "    for vote in classList:\n",
    "        if vote not in classCount.keys(): classCount[vote] = 0\n",
    "        classCount[vote] += 1\n",
    "    sortedClassCount = sorted(classCount.iteritems(), key=operator.itemgetter(1), reverse=True)\n",
    "    return sortedClassCount[0][0]\n",
    "\n",
    "\n",
    "def createTree(dataSet, labels):\n",
    "    # extracting data\n",
    "    classList = [example[-1] for example in dataSet]\n",
    "    if classList.count(classList[0]) == len(classList):\n",
    "        return classList[0]  # stop splitting when all of the classes are equal\n",
    "    if len(dataSet[0]) == 1:  # stop splitting when there are no more features in dataSet\n",
    "        return majorityCnt(classList)\n",
    "    # use Information Gain\n",
    "    bestFeat = chooseBestFeatureToSplit(dataSet)\n",
    "    bestFeatLabel = labels[bestFeat]\n",
    "\n",
    "    #build a tree recursively\n",
    "    myTree = {bestFeatLabel: {}}\n",
    "    #print(\"myTree : \"+labels[bestFeat])\n",
    "    del (labels[bestFeat])\n",
    "    featValues = [example[bestFeat] for example in dataSet]\n",
    "    #print(\"featValues: \"+str(featValues))\n",
    "    uniqueVals = set(featValues)\n",
    "    #print(\"uniqueVals: \" + str(uniqueVals))\n",
    "    for value in uniqueVals:\n",
    "        subLabels = labels[:]  # copy all of labels, so trees don't mess up existing labels\n",
    "        #print(\"subLabels\"+str(subLabels))\n",
    "        myTree[bestFeatLabel][value] = createTree(splitDataSet(dataSet, bestFeat, value), subLabels)\n",
    "        #print(\"myTree : \" + str(myTree))\n",
    "    return myTree\n",
    "\n",
    "\n",
    "\n",
    "# collect data\n",
    "myDat, labels = createDataSet()\n",
    "\n",
    "#build a tree\n",
    "mytree = createTree(myDat, labels)\n",
    "print(mytree)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Quellen: Softcomputing in der Informatik (Jurgen Paetz) Springer\n",
    "         "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": false
   },
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.6.0"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
