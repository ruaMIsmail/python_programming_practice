'''For this challenge you will determine what nodes are farthest apart.
have the function FarthestNodes(strArr) read strArr which will be an array of hyphenated letters representing paths
between those two nodes. For example: ["a-b","b-c","b-d"] means that there is a path from node a to b (and b to a),
b to c, and b to d. Your program should determine the longest path that exists in the graph and return the length of that path.
So for the example above, your program should return 2 because of the paths a-b-c and d-b-c.
The path a-b-c also means that there is a path c-b-a. No cycles will exist in the graph and every node will be connected
to some other node in the graph.
'''
from collections import defaultdict, deque

graph = defaultdict(list)


def add_edge(graph, u_node, vertices):
    graph[u_node].append(vertices)
    graph[vertices].append(u_node)


def letter_to_int(letter):
    alphabet = list('abcdefghijklmnopqrstuvwxyz')
    return alphabet.index(letter)


def FarthestNodes(edges):
    extact = []
    for elm in edges:
        f, s = elm.split('-')
        extact.append((f, s))
    for index, tuple in enumerate(extact):
        elm_one = tuple[0]
        elm_two = tuple[1]
        add_edge(graph, letter_to_int(elm_one), letter_to_int(elm_two))

    def BFS(u_node):
        '''
        one approach is to treat each node as a possible starting point from where we can expand and perform BFS
        at each step of our BFS we update the cost of each node
        this cost determines the length from the current starting node
        we repeat this process for all the nodes in our graph and keep track of the highest length
        :param u_node: node to start the BFS
        :return: max distance given a node after running BFS
        '''
        vertices = len(graph)
        visited = [False for i in range(vertices + 1)]
        distance = [-1 for i in range(vertices + 1)]

        distance[u_node] = 0
        queue = deque()
        queue.append(u_node)
        visited[u_node] = True
        while queue:
            front = queue.popleft()
            for i in graph[front]:
                if not visited[i]:
                    visited[i] = True
                    distance[i] = distance[front] + 1
                    queue.append(i)
        maxdistance = 0

        for i in range(vertices):
            if distance[i] > maxdistance:
                maxdistance = distance[i]
                node_index: int = i

        return node_index, maxdistance

    node, dis = BFS(0)
    node_2, long_dis = BFS(node)
    return long_dis

# Press the green button in the gutter to run the script.
if __name__ == '__main__':
    strArr = ["a-b","b-c","b-d"]
    print(FarthestNodes(strArr))

