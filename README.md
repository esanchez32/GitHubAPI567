import unittest
from GitHubAPI import github_repos, github_commits


class Testing(unittest.TestCase):

    def TestRepositories(self):
        repositories = github_repos("esanchez32")
        self.assertEqual(len(repositories), 5, "Username esanchez32 has 5 repositories")
        self.assertIn("HW00_HelloWorld", repositories)
        self.assertIn('Triangle567', repositories)
        self.assertIn("GEDCOME", repositories)
        self.assertIn("TriangleTesting", repositories)
        self.assertIn("GitHubAPI567", repositories)

    def TestRepositories2(self):
        repositories = github_repos("richkempinski")
        self.assertEqual(len(repositories), 5, "Username richkempinski has 5 repositories")
        self.assertIn("threads-of-life", repositories)
        self.assertIn("hellogitworld", repositories)
        self.assertIn("Mocks", repositories)
        self.assertIn("Project1", repositories)
        self.assertIn("helloworld", repositories)

    def TestCommits(self):
        self.assertEqual(github_commits("esanchez32", "HW00_HelloWorld"), 2)
        self.assertEqual(github_commits("esanchez32", "Triangle567"), 13)
        self.assertEqual(github_commits("esanchez32", "GEDCOME"), 2)
        self.assertEqual(github_commits("esanchez32", "TriangleTesting"), 2)
        self.assertEqual(github_commits("esanchez32", "GitHubAPI567"), 3)

    def TestCommits2(self):
        self.assertEqual(github_commits("richkempinski", "threads-of-life"), 1)
        self.assertEqual(github_commits("richkempinski", "hellogitworld"), 50)
        self.assertEqual(github_commits("richkempinski", "Mocks"), 8)
        self.assertEqual(github_commits("richkempinski", "Project1"), 2)
        self.assertEqual(github_commits("richkempinski", "helloworld"), 6)


if __name__ == "__run__":
   unittest.main()




