# LCS Draft 3 - Target Naming

Contact: Connor Horman <chorman@lcdev.xyz>

Targets: Toolchains and Target Naming  Working Committee

Start Date: 2023-11-05

Last Review Date:

Last Revision Date: 2023-11-05

Revision Number: 0

## §1 Canonical Target Names

A canonical target name shall be a 3 or 4 segment name, separated by `-`s, where each segment consists of ASCII letters, numbers, the `_` character, and the `.` character.

The segments of a Canonical Target Name are:
* The architecture of the target
* The vendor of the target platform
* The System, if any
* The Environment.

The System or the Environment field may be omitted from any canonical target, but at least one must be present, as appropriate.

An environment is information about the target. It may include:
* A further discrimination of the system, such as an abi or standard library,
* An object format specification, and
* A abi subfield, for example, identifying the x32 abi for `x86_64`.

Toolchains that support a target should accept the target in its canonical form.

## §2 Noncanonical Target Names

A noncanonical target name is a target name in the same format as a canonical target name, except:
* One or more fields may be omitted (but the target may not be empty),
* One or more fields may be an alias of the canonical name, 
* One or more fields may contain additional characters, such as `/`, and
* One or more fields may be fused into a single field.

Each Noncanonical Target matches exactly one canonical target, the translation process prescribed herein converts a noncanonical target to a canonical one.

The canonicalization process is as follows:
1. Component Splitting - Each fused component is split according to the prescriptions in §3.
2. Component Inference - Each omitted component which may be inferred from present ones is inserted according to the prescriptions in §3.
3. Component Canonicalization - Each aliased/noncanonical component is replaced with its canonical name according to the prescriptions in §3.
4. Any additional steps according to the prescriptions in §3.

## §3 Special Publications Prescribing Canonical Forms

The Toolchains and Target Naming Working Committee may make special publications regarding the process and forms for canonicalizing targets, including:
* The name of fused components, and the result of splitting fused components,
* The Result of inferring absent components, as applicable,
* The name of component aliases of canonical components,
* The name of canonical components, and
* Additional canonicalization steps which need to be prescribed.

Additionally, the Toolchains and Target Naming Working Committee should maintain the information above, except as to canonicalization steps, in a machine readable format, and may maintain computer programs which perform the translation of noncanonical targets (or a subset thereof) to canonical targets and support compiler toolchains and other programs that use canonical and noncanonical targets.