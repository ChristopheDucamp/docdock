+++
draft = false
title = "mermaid"
description = ""

[menu.main]
parent = "shortcodes"
identifier = "mermaid"
+++

## Exemple GANTT

	{{</*mermaid*/>}}
	gantt
	        dateFormat  YYYY-MM-DD
	        title Ajout fonctionnalité de diagramme de GANTT à mermaid
	        section A section
	        Completed task            :done,    des1, 2014-01-06,2014-01-08
	        Active task               :active,  des2, 2014-01-09, 3d
	        Future task               :         des3, after des2, 5d
	        Future task2               :         des4, after des3, 5d
	        section Critical tasks
	        Completed task in the critical line :crit, done, 2014-01-06,24h
	        Implement parser and jison          :crit, done, after des1, 2d
	        Create tests for parser             :crit, active, 3d
	        Future task in critical line        :crit, 5d
	        Create tests for renderer           :2d
	        Add to mermaid                      :1d
	{{</* /mermaid */>}}


{{<mermaid>}}
gantt
        dateFormat  YYYY-MM-DD
        title Ajout fonctionnalité de diagramme de GANTT à mermaid
        section A section
        Completed task            :done,    des1, 2014-01-06,2014-01-08
        Active task               :active,  des2, 2014-01-09, 3d
        Future task               :         des3, after des2, 5d
        Future task2               :         des4, after des3, 5d
        section Critical tasks
        Completed task in the critical line :crit, done, 2014-01-06,24h
        Implement parser and jison          :crit, done, after des1, 2d
        Create tests for parser             :crit, active, 3d
        Future task in critical line        :crit, 5d
        Create tests for renderer           :2d
        Add to mermaid                      :1d
{{</mermaid>}}

## Exemple de séquence

	{{</*mermaid*/>}}
	sequenceDiagram
	    participant Alice
	    participant Bruno
	    Alice->John: Hello John, how are you?
	    loop Healthcheck
	        John->John: Fight against hypochondria
	    end
	    Note right of John: Rational thoughts <br/>prevail...
	    John-->Alice: Great!
	    John->Bruno: How about you?
	    Bruno-->John: Jolly good!
	{{</* /mermaid */>}}


{{<mermaid>}}
sequenceDiagram
    participant Alice
    participant Bruno
    Alice->John: Hello John, how are you?
    loop Healthcheck
        John->John: Fight against hypochondria
    end
    Note right of John: Rational thoughts <br/>prevail...
    John-->Alice: Great!
    John->Bruno: How about you?
    Bruno-->John: Jolly good!
{{< /mermaid >}}

## Exemple de Flowchart

	{{</*mermaid*/>}}
	graph TD;
	    A-->B;
	    A-->C;
	    B-->D;
	    C-->D;
    {{</* /mermaid */>}}

{{<mermaid>}}
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
{{< /mermaid >}}