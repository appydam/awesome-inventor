# awesome-inventor
package assignments;

import java.util.Scanner;

public class ReadThePages {

	public static void main(String[] args) {

		Scanner scn = new Scanner(System.in);

		int nob = scn.nextInt();

		long nos = scn.nextLong();

		long[] pages = new long[nob];

		for (int i = 0; i < pages.length; i++) {

			pages[i] = scn.nextInt();

		}

		System.out.println(ac(pages, nob, nos));

	}

	public static long ac(long[] pages, int nob, long nos) {

		long lo = 0;

		long hi = 0;

		for (long val : pages) {

			hi += val;

		}

		long finalAns = 0;

		while (lo <= hi) {

			long mid = (lo + hi) / 2;

			if (isPossible(pages, nob, nos, mid)) {

				hi = mid - 1;

				finalAns = mid;

			} else {

				lo = mid + 1;

			}

		}

		return finalAns;

	}

	private static boolean isPossible(long[] pages, int nob, long nos, long mid) {

		long noOfStudents = 1;

		long pagesRead = 0;

		for (int i = 0; i < pages.length; i++) {

			if (pages[i] > mid) {

				return false;

			}

			if (pagesRead + pages[i] <= mid) {

				pagesRead += pages[i];

			} else {

				noOfStudents++;

				pagesRead = pages[i];

				if (noOfStudents > nos) {

					return false;

				}

			}

		}

		return true;

	}

}
